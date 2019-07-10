---
layout: post
title: 性能优化
categories: 性能优化
description: 性能优化
keywords: 性能优化
---

***彼此都有意而不说出来是爱情最高境界，因为这个时候两人都在尽情享受媚眼，尽情享受目光相对时火热心理，尽情享受手指相碰时惊心动魄。一旦说出来，味道会淡许***

## 1、[如何使用 jstack 分析线程状态](https://www.cnblogs.com/wuchanming/p/7766994.html)
>1、top 默认按cpu使用率排序    
2、top -Hp pid  例子：top -Hp 7568  查看该进程下各个线程的cpu使用情况（会发现 7594 的进程占用的 cpu 最高）  
3、jstack 7568 > a.txt  打印进程的对战信息到 a.txt 文件中  
4、printf %x pid  例子：printf %x 7594（1d90 步骤二发现的）   10 进制转换为 16 进制，因为打印出来的堆栈信息里面的 pid 是 16 进制的  
5、less a.txt  查看 a.txt  
6、/关键词（1d90）  enter （回车搜索） N 向上搜索 n向下搜索，找到这个线程，查看具体的堆栈信息  

## 2、[Linux 下如何查看哪个进程占用内存多？](https://blog.csdn.net/qq_37960324/article/details/85156932)
## 3、[linux 实时监控系统IO状态和IO性能（iostat命令解析）](https://blog.csdn.net/li_wen01/article/details/82683627)
## 4、[CentOS 7 安装部署 zabbix3.4 性能监控](https://blog.51cto.com/andyxu/2120362)



