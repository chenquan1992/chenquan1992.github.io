---
layout: post
title: MongoDB 基本操作
categories: MongoDB
description: MongoDB
keywords: MongoDB
---

***画虎画皮难画骨，知人知面不知心。钱财如粪土，仁义值千金。***

## 基本命令操作
```text
show dbs;                  #查看全部数据库

show collections;          #显示当前数据库中的集合（类似关系数据库中的表）

show users;                #查看当前数据库的用户信息

use <db name>;             #切换数据库跟mysql一样

db;或者db.getName();        #查看当前所在数据库

db.help();                 #显示数据库操作命令，里面有很多的命令 
db.foo.help();             #显示集合操作命令，同样有很多的命令，foo指的是当前数据库下，一个叫foo的集合，并非真正意义上的命令 
db.foo.find();             #对于当前数据库中的foo集合进行数据查找（由于没有条件，会列出所有数据） 
db.foo.find( { a : 1 } );  #对于当前数据库中的foo集合进行查找，条件是数据中有一个属性叫a，且a的值为1
db.zhipin_data.drop() 	   #删除 zhipin_data 这张表
```