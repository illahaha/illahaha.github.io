---
layout: post
title: "android install apk"
description: "android install apk"
category: "android"
tags: [install]
---
{% include JB/setup %}
---

*   基本信息
*	adb安装
*	静默安装
*	启动


----------

#基本信息#
adb install 调用的是内部的 pm install。详细信息参看:

>[http://blog.csdn.net/new_abc/article/details/7435508][1]

xml中获取信息：
例子：

    <application android:theme="@style/AppTheme" android:label="@string/app_name" android:icon="@drawable/icon" android:name="com.ccb.android.message.activity.MessageApplication" android:persistent="true" android:allowBackup="true">
    <activity android:theme="@*android:style/Theme.NoTitleBar.Fullscreen" android:label="@string/title_activity_start_anim" android:name="com.ccb.android.message.activity.StartAnimActivity">
    <intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
    </activity>
    <activity android:label="@string/app_name" android:name="com.ccb.android.message.activity.LoginActivity" android:launchMode="singleTask" android:screenOrientation="portrait" android:windowSoftInputMode="adjustPan" />
    <activity android:label="@string/app_name" android:name="com.ccb.android.message.activity.RegisterActivity" android:launchMode="singleTask" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden|adjustPan" />
    <activity android:label="@string/app_name" android:name="com.ccb.android.message.activity.CreditCardAuthActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/app_name" android:name="com.ccb.android.message.activity.AccountActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/title_activity_tab_host" android:name="com.ccb.android.message.activity.TabHostActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/title_activity_my_message" android:name="com.ccb.android.message.activity.MyMessageActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/app_name" android:name="com.ccb.android.message.activity.MoreServiceActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/title_activity_my_detail_msg" android:name="com.ccb.android.message.activity.MyDetailMsgActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="@string/title_activity_about" android:name="com.ccb.android.message.activity.AboutActivity" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <activity android:label="title_activity_moreservicegroup" android:name="com.ccb.android.message.activity.MoreServiceActivityGroup" android:launchMode="singleTask" android:screenOrientation="portrait" />
    <service android:name="com.ccb.android.message.utils.MyMsgService" android:enabled="true">
    <intent-filter>
    <action android:name="com.ccb.android.message.udpconnection.MyUdpService" />
    </intent-filter>
    </service>
    <service android:name="com.ccb.android.message.utils.DaemonService" />
    <receiver android:name="com.ccb.android.message.receiver.BootReceiver">
    <intent-filter android:priority="2147483647">
    <action android:name="android.intent.action.SCREEN_ON" />
    <action android:name="android.intent.action.SCREEN_OFF" />
    <action android:name="android.intent.action.USER_PRESENT" />
    </intent-filter>
    </receiver>
    <service android:name="com.baidu.location.f" android:enabled="true" android:process=":remote" />
    <activity android:label="@string/title_activity_my_msg_activity_group" android:name="com.ccb.android.message.activity.MyMsgActivityGroup" />
    <receiver android:name="com.ccb.android.message.receiver.DownLoadReceiver">
    <intent-filter>
    <action android:name="android.intent.action.DOWNLOAD_COMPLETE" />
    <category android:name="android.intent.category.DEFAULT" />
    </intent-filter>
    </receiver>
    </application>

在例子中，可以找到包名在节点“application”的属性“android:name=”。
在“activity”节点的子节点有
	android.intent.action.MAIN
说明是启动类，在启动过程中会用到。

#adb 安装#
	adb install -r apk name

例如：
	
	adb install -r test.apk

#pm 安装#
	pm install -r apk name
例如:

	pm install -r "/data/local/tmp/test.apk"

#启动#

	am start -D -n "com.example.testinject/com.example.testinject.MainActivity" 

---
[1]:http://blog.csdn.net/new_abc/article/details/7435508