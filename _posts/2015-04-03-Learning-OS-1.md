---
layout: post
title: "Learning OS - 1"
modified:
categories: 
description: "Learning operation system - 2"
tags: [uCoreOS,operation system]
image:
  feature:
  credit:
  creditlink:
comments:
share:
published: true
---
这回接着上回的来，在做好所有的预备工作之后，开始了lab1的工作
本次实验主要时完成了bootloader的工作，在系统加电之后，电脑所进行的工作，
加载BIOS,加载bootloader，之后将操作系统读入内存中..

<!--more-->

##练习1

练习1的主要任务是理解make生成执行文件的过程，理解makefile中各个命令，依赖，目标的生成关系。

makefile中关键命令

*   shell

~~~ shell
CFLAGS	+= $(shell $(CC) -fno-stack-protector -E -x c /dev/null >/dev/null 2>&1 && echo -fno-stack-protector)
~~~

CFLAGS的意思是使用shell 命令运行后面的参数得到的参数

*  赋值

~~~ shell
CF  =  $(A) #直接赋值，在调用时展开
CF  := $(A) #直接赋值，在声明时展开
CF  ?= $(A) #当CF为空时，赋值
CF  += $(A) #在末尾追加A的内容
~~~

=赋值时，不会展开A的值，而:=会展开A的值。

*  call

~~~ shell
objfile = $(call toooj,$(1))
~~~

call 是调用makefile中自定义或内置的函数，
许多函数的定义都是在tools/function.mk中的

附带函数声明一个:

~~~ shell
define cc_template
$$(call todep,$(1),$(4)): $(1) | $$$$(dir $$$$@)
	@$(2) -I$$(dir $(1)) $(3) -MM $$< -MT "$$(patsubst %.d,%.o,$$@) $$@"> $$@
$$(call toobj,$(1),$(4)): $(1) | $$$$(dir $$$$@)
	@echo + cc $$<
	$(V)$(2) -I$$(dir $(1)) $(3) -c $$< -o $$@
endef
~~~


*   patsubst

~~~ shell
cgtype = $(patsubst %.$(2),%.(3),$(1))
$(patsubst <pattern>,<replacement>,<text>)
~~~

patsubst 将text中符合pattern的文本转换成replacement的文本

*   wildcard

~~~ shell
src = $(wildcard *.c ./sub/*.c)
~~~

wildcard 时通配符，寻找所有匹配的文件

*   引用参数

~~~ shell
a.txt : b.txt c.txt
$@ #当前目标 a.txt
$< #第一个前置条件 b.txt
$? #比目标更新的所有前置条件
$^ #所有的前置条件 b.txt c.txt
$* #指代%匹配的部分 
$(@D) #指向$@的目录名
$(@F) #指向$@的文件名
$(<D) #指向$<的目录名
$(<F) #指向$<的文件名
~~~

*   判断和循环

~~~ shell
ifeq ($(CC),gcc)
    libs=$(libs_for_gcc)
else 
    libs=$(normal_libs)
endif

LIST = one two three
all:
    for i in $(LIST); do \
        echo $$i; \
    done
~~~

<figure>
    <img src=”http://0.0.0.0:4000/image/triangular.png” alt=””>
</figure>
