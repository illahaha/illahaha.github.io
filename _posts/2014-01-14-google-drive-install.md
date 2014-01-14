---
layout: post
title: "Google Drive install"
description: "Google Drive install in ch"
category: "技巧"
tags: [Google Drive]
---
{% include JB/setup %}

---

#Google Drive 被墙后下载方式

----

-	hosts修改

-	下载完整安装包

----

###hosts修改###

>	win7 x64 修改方式C:\Windows\System32\drivers\etc找到hosts文件，复制到桌面，添加如下：

	173.194.38.128		drive.google.com

>	将修改后的hosts复制回去，替换原来的.

###下载完整安装包###

>	1.在

	http://www.softpedia.com/get/Internet/File-Sharing/Google-Drive.shtml

>	获取google drive的最新版本号，比如

	Google Drive 1.13.5782.0599

>	2.根据***1***中的方法得到如下

	http://dl.google.com/drive/1.13.5782.0599/gsync.msi

>	在浏览器中打开下载.
