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

---

#基本信息#
adb install 调用的是内部的 pm install。详细信息参看:
[http://blog.csdn.net/new_abc/article/details/7435508][1]

#adb 安装#
	adb install -r package

#pm 安装#
	pm install -r package

---
[1]:http://blog.csdn.net/new_abc/article/details/7435508