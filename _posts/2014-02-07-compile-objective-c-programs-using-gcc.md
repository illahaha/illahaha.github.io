---
layout: post
title: "Compile Objective C Programs Using gcc"
description: "Compile Objective C Programs Using gcc"
category: "Objective C"
tags: [Objective C]
---
{% include JB/setup %}

---
*	编译环境
*	mac os x 编译
*	linux编译
*	windows编译

---

#编译环境

>	1.	install GNUstep [http://www.gnustep.org/][0]
>	2.	a sample
>	
		#import <Foundation/Foundation.h>
 		@interface HelloWorld : NSObject
 			- (void) hello;
 		@end
>
	 	@implementation HelloWorld
			- (void) hello {
		NSLog(@"hello world!");
 		}
>
 		@end
 		int main(void) {
 			HelloWorld *hw = [[HelloWorld alloc] init];
 			[hw hello];
			[hw release];
 		}
>

#mac os x 编译

>mac os x 上的编译
>
>		gcc -o hello hello.m -framework Foundation

#linux编译

>linux 上的编译
>
>		gcc -o hello hello.m -I /usr/lib/GNUstep/System/Library/Headers \
		-L /usr/lib/GNUstep/System/Library/Libraries/ -lgnustep-base \
		-fconstant-string-class=NSConstantString

>or

>		gcc -o hello hello.m -I /usr/include/GNUstep/ -L /usr/lib/GNUstep/ \
		-lgnustep-base -fconstant-string-class=NSConstantString

#windows编译

>		gcc `gnustep-config --objc-flags` -o hello2 hello2.m -L /GNUstep/System/Library/Libraries -lobjc -lgnustep-base
>		
>**Be very careful about the -lobjc and -lgnustep-base switch, they must appear after file name "hello.m", otherwise linking will fail.**

---
from:[http://www.cnblogs.com/jack204/archive/2012/3/21.html][1]

---
[0]:http://www.gnustep.org/
[1]:http://www.cnblogs.com/jack204/archive/2012/3/21.html