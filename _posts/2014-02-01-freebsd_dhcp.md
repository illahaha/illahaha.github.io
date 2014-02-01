---
layout: post
title: "freebsd_dhcp"
description: "dhcp"
category: "freebsd"
tags: [dhcp]
---
{% include JB/setup %}
---

*	dhcp设置

---

##DHCP配置
>	编辑*/etc/rc.conf*
>
	ifconfig_fxp0="DHCP"
>	fxp0 替换为您希望自动配置的网络接口的名字
