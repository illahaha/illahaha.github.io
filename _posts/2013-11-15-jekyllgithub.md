---
layout: post
title: "jekyll搭建github博客"
description: "github学习"
category: "github"
tags: [jekyll]
---
{% include JB/setup %}
---
*	-搭建环境
*	-搭建过程
*	-后记
---
## 搭建环境

###### github配置
1. 注册github帐号.
2. 创建一个名字为*帐号名.github.io*的repository.
3. 按下一步注册成功，此时不要选github上提供的模板，不灵活.

###### jekyll配置
1. Ruby
2. Bundler
   >  gem install bundler
3. Jekyll

## 搭建过程
1. [模板选择][1]
2. 在*Using Themes*选择*Find Themes*挑选一个安装.
3. 修改Themes的版本信息等内容，注意那些内容在根目录下的配置里修改.
4. 提交自定义修改后的模板.
---
## 后记
   github 上的blog是不限流量可自定义代码的平台，适合码农玩。

[1]:http://jekyllbootstrap.com
