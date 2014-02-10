---
layout: post
title: "mac osx bitnami redmine svn error"
description: "svn server"
category: "mac os x"
tags: [svn server]
---
{% include JB/setup %}

---

*	错误修复

---

##错误修复##

>错误信息：
>
>		scm不可用，检查控制面板
>
>错误修复:
>
>		1. 在<installdir>/apps/redmine/htdocs/lib/redmine/scm/adapters/subversion_adapter.rb中
>		2.找到位置
>			27:-        SVN_BIN = Redmine::Configuration['scm_subversion_command'] || "svn"  
>			27:+        SVN_BIN = Redmine::Configuration['scm_subversion_command'] || "<installdir>/subversion/bin/svn"
>		3.重启apache
>			<installdir>/ctlscript.sh restart apache

---