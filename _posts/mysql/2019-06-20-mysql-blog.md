---
layout: post
title: Mysql 优化博客
categories: Mysql 优化博客
description: Mysql 优化博客
keywords: Mysql 
---

***生命中是否会有一个人，当你第一眼看到他时，你已经知道，就是他了。这时，你微笑的眼睛望着他，笃定地说：“你哪里都别想再去了！”***  

分区表 可以提高性能 [详情](https://blog.csdn.net/jhq0113/article/details/44593511)  
主从复制（读写分离）  
>在业务复杂的系统中，有这么一个情景，有一句sql语句需要锁表，导致暂时不能使用读的服务，那么就很影响运行中的业务，使用主从复制，让主库负责写，从库负责读，这样，即使主库出现了锁表的情景，通过读从库也可以保证业务的正常运作。   
>[详情](https://blog.csdn.net/u014508939/article/details/61938285)  
>[详情](https://blog.csdn.net/qq_38056704/article/details/80730578) 
       
[一次非常有意思的sql优化经历](https://www.cnblogs.com/tangyanbo/p/4462734.html)  
[mysql索引类型 normal, unique, full text](https://www.cnblogs.com/cq-home/p/3482101.html)  
[mysql数据库分库分表(Sharding)](https://www.cnblogs.com/mfmdaoyou/p/7246711.html)  
[MySQL大数据量分页性能优化](https://www.cnblogs.com/lpfuture/p/5772055.html)  
[SQL系列目录](https://www.cnblogs.com/zhangs1986/p/4914125.html)  
[sql 报表](https://blog.csdn.net/qq_36445227/article/details/80993925)  
[Mysql慢查询日志的使用 和 Mysql的优化](https://blog.csdn.net/m_nanle_xiaobudiu/article/details/79288257)  
[mysql备份恢复详解](https://www.cnblogs.com/coshaho/p/7302419.html)  
[MySQL高可用解决方案之keepalive+lvs+mysql](https://blog.csdn.net/Zhou20072724/article/details/84165293)  
[maxscale 实现读写分离](https://www.cnblogs.com/itfenqing/p/6140029.html)  
[MySQL 高可用：mysql+mycat实现数据库分片（分库分表）](https://blog.csdn.net/kk185800961/article/details/51147029) 


[MySQL 中进行树状所有子节点的查询 MySQL 树查询所有子](https://blog.csdn.net/javadhh/article/details/48622743) 


        
    


