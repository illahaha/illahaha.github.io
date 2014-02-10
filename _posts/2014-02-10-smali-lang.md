---
layout: post
title: "smali lang"
description: "smali 语法分析"
category: "android"
tags: [smali]
---
{% include JB/setup %}
---

*	例子
*	例子分析
*	语法总结

---

#例子

>	##java代码##

    package com.cn.daming.activity;
    
    import android.app.Activity;
    import android.os.Bundle;
    import android.widget.TextView;
    
    public class HelloWorldAppActivity extends Activity {
    	private TextView mTextView;
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.main);
    mTextView = (TextView)findViewById(R.id.text_view);
    mTextView.setText(R.string.hello);
    }
    }

>	##smali代码##

    .class public Lcom/cn/daming/activity/HelloWorldAppActivity;
    .super Landroid/app/Activity;
    .source "HelloWorldAppActivity.java"
    
    
    # instance fields
    .field private mTextView:Landroid/widget/TextView;
    
    
    # direct methods
    .method public constructor <init>()V
    .locals 0
    
    .prologue
    .line 7
    invoke-direct {p0}, Landroid/app/Activity;-><init>()V
    
    return-void
    .end method
    
    
    # virtual methods
    .method public onCreate(Landroid/os/Bundle;)V
    .locals 2
    .parameter "savedInstanceState"
    
    .prologue
    .line 12
    invoke-super {p0, p1}, Landroid/app/Activity;->onCreate(Landroid/os/Bundle;)V
    
    .line 13
    const/high16 v0, 0x7f03
    
    invoke-virtual {p0, v0}, Lcom/cn/daming/activity/HelloWorldAppActivity;->setContentView(I)V
    
    .line 14
    const/high16 v0, 0x7f05
    
    invoke-virtual {p0, v0}, Lcom/cn/daming/activity/HelloWorldAppActivity;->findViewById(I)Landroid/view/View;
    
    move-result-object v0
    
    check-cast v0, Landroid/widget/TextView;
    
    iput-object v0, p0, Lcom/cn/daming/activity/HelloWorldAppActivity;->mTextView:Landroid/widget/TextView;
    
    .line 15
    iget-object v0, p0, Lcom/cn/daming/activity/HelloWorldAppActivity;->mTextView:Landroid/widget/TextView;
    
    const/high16 v1, 0x7f04
    
    invoke-virtual {v0, v1}, Landroid/widget/TextView;->setText(I)V
    
    .line 16
    return-void
    .end method

>	##例子分析##
>	
>p0 = this
>		
>private TextView mTextView;
>
>对应的smali代码是：
>
>.field private mTextView:Landroid/widget/TextView;
>
>由此可以看出，smali中会对类TextView展开为路径模式，在编译为dex的时候，会在android/widget目录下找TextView.Smali进行关联。
>
>语法格式：
>
>[实例]:[实例类型]
>
>接下来分析OnCreate
>
>在OnCreate中，开始的.locals 2 表明此函数用到两个本地寄存器 v0 v1。
>
>super.onCreate(savedInstanceState);
>
>对应的smali是
>
>invoke-super {p0, p1}, Landroid/app/Activity;->onCreate(Landroid/os/Bundle;)V
>
>这句代码含义是
>
>p0作为this指针,p1作为输入的参数savedInstanceState,调用的方法是父类Activity的onCreate.
>
>setContentView(R.layout.main);

>对应的smali是
>
>const/high16 v0, 0x7f03
>
>invoke-virtual {p0, v0}, Lcom/cn/daming/activity/HelloWorldAppActivity;->setContentView(I)V
>
>这句代码的含义是
>
>0x7f03 表示 R.layout.main这个参数，猜测可能是地址。
>
>p0依然是this指针，v0是参数，后面是调用的具体类方法。
>
>可以看出invoke语法:
>
>invoke-xxx {实例this,参数}, {类} {方法}
>
>mTextView = (TextView)findViewById(R.id.text_view);
>
>对应的smali是：
>
>const/high16 v0, 0x7f05
>
>invoke-virtual {p0, v0}, Lcom/cn/daming/activity/HelloWorldAppActivity;->findViewById(I)Landroid/view/View;
>
>move-result-object v0
>
>check-cast v0, Landroid/widget/TextView;
>
>iput-object v0, p0, Lcom/cn/daming/activity/HelloWorldAppActivity;->mTextView:Landroid/widget/TextView;
>
>这句代码的含义：
>
>0x7f05是r.id.text_view
>
>invoke-virtual 是调用findviewbyid方法
>
>move-result-object 是将调用invoke后的结果存储在v0中，此时v0是TextView类型的值。
>
>check-cast就是强制转换(TextView)检查语句。
>
>iput-object就是对mTextView赋值语句。
>
>此时分析的差不多了，对应关系.line中，会将java代码与smali代码进行对应分割。所以smali表示的气势就是dex的opcode形式。

>##语法总结##
[http://blog.csdn.net/wdaming1986/article/details/8299996][0]

[0]:http://blog.csdn.net/wdaming1986/article/details/8299996