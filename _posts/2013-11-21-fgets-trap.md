---
layout: post
title: "fgets trap"
description: "trap"
category: "code"
tags: [fgets]
---
{% include JB/setup %}
---
*	-fgets用法
*	-fgets陷阱
*	-fgets后记
---
##feges用法

    man fgets

##fgets陷阱

  当字符串中含有回车的hex数值*0d*时，fgets会误认为是一行。

##fgets后记
  复杂处理不可用fgets。
 