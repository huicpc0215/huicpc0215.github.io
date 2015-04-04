---
layout: post
title: "Learning OS - 0"
description: "Learning operation system one by one"
modified: 2015-03-31
tags: [uCoreOS,operation system]
image:
  feature: abstract-4.jpg
  credit: dargadgetz
share:
  published: true
---

#目的

最近看了一下uCoreOS，是清华大学在xuetangx.com上开设的一门操作系统课程的实验，想跟着做一下，感受一下清华大学学生的厉害之处。
顺便补补自己本科阶段没有学习过的操作系统这么久仰已久的课程。


<!--more-->


#过程

首先根据[uCoreOS-guide](https://www.gitbook.com/book/objectkuan/ucore-docs/details)上面的lab0准备，

需要了解很多相关预备知识具体有以下几点（点击目标，了解更多）:

1.  命令行 bash shell [ref_0](http://wiki.ubuntu.org.cn/Shell%E7%BC%96%E7%A8%8B%E5%9F%BA%E7%A1%80)  [ref_1](http://wiki.ubuntu.org.cn/%E9%AB%98%E7%BA%A7Bash%E8%84%9A%E6%9C%AC%E7%BC%96%E7%A8%8B%E6%8C%87%E5%8D%97)
2.  git 分布式版本控制系统 [ref_0](http://www.cnblogs.com/cspku/articles/Git_cmds.html) [ref_1](http://www.worldhello.net/gotgithub/index.html)
3.  代码阅读与编辑工具:
    1.  eclise-cdt [ref_0](http://blog.csdn.net/anzhu_111/article/details/5946634)
    2.  understand [ref_0](http://blog.csdn.net/qwang24/article/details/4064975)
    3.  vim [ref_0](http://www.httpy.com/html/wangluobiancheng/Perljiaocheng/2014/0613/93894.html) [ref_1](http://wenku.baidu.com/view/4b004dd5360cba1aa811da77.html)
    4.  gedit 
4.  源码比较和补丁工具:
    1.  diff patch [ref_0](http://www.ibm.com/developerworks/cn/linux/l-diffp/index.html) [ref_1](http://www.cnblogs.com/itech/archive/2009/08/19/1549729.html)
    2.  meld(gui) [ref_0](https://linuxtoy.org/archives/meld-2.html)
5.  开发，编译，调试工具:gcc,gdb,make
    1.  gcc C编译器 [ref_0](http://wiki.ubuntu.org.cn/Gcchowto) [ref_1](http://wiki.ubuntu.org.cn/Compiling_Cpp) [ref_2](http://wiki.ubuntu.org.cn/C_Cpp_IDE) [ref_3](http://wiki.ubuntu.org.cn/C%E8%AF%AD%E8%A8%80%E7%AE%80%E8%A6%81%E8%AF%AD%E6%B3%95%E6%8C%87%E5%8D%97)
    2.  gdb debug工具 [ref_0](http://wiki.ubuntu.org.cn/%E7%94%A8GDB%E8%B0%83%E8%AF%95%E7%A8%8B%E5%BA%8F)
    3.  ld 链接器
    4.  objdump 对ELF文件反编译，转换执行格式工具
    5.  nm 查看执行文件变量 函数的地址
    6.  readelf 分析elf格式的执行文件 
    7.  make&&makefile 集成编译命令 [ref_0](http://wiki.ubuntu.com.cn/index.php?title=%E8%B7%9F%E6%88%91%E4%B8%80%E8%B5%B7%E5%86%99Makefile&variant=zh-cn) [ref_1](http://blog.csdn.net/a_ran/article/details/43937041)
    8.  dd 读写数据到文件和设备中 
6.  qemu 硬件模拟器，模拟x86-32计算器 [ref_0](http://wenku.baidu.com/view/04c0116aa45177232f60a2eb.html)


## bash 

Bourne Again SHell的缩写,是一种linux上最常见的shell之一. 通常文件后缀为.sh是可执行shell.

## git

git 是一种分布式版本控制系统,主要理解分支(branch),合并(merge),提交(push),更新(pull),注释(commit)

## 代码阅读工具

暂时值会熟悉vim的基本操作,GUI的工具还没有使用过.

## 源码比较工具

diff patch 在参考上说的比较详细了,认真阅读即可.

## 开发编译调试

gcc,只用过一些基本命令-o输出定向到某文件 -g 添加调试信息便于gdb配合使用

gdb配合 -tui 调试起来非常方便.n next, b break 在行号/函数设置断点 , watch 某个变量或者表达式, c continue 继续运行直至断点. 

make根据makefile 的规则,一步步根据依赖关系,组建整个工程.其他的工具暂时还没有用到.(具体在make参考中有说明)


## qemu硬件模拟器

需要使用qemu-system-x86_32代替qemu模拟器


