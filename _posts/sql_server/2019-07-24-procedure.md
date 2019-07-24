---
layout: post
title: sql server 存储过程
categories: sqlserver
description: sql server 存储过程
keywords: sql server
---

***爱情本来并不复杂，来来去去不过三个字，不是我爱你，我恨你，便是算了吧，你好吗，对不起***  

### sql server 分页语句
```sql
-- 分页查询（通用型）
SELECT TOP
	pageSize * 
FROM
	( SELECT row_number () OVER ( ORDER BY sno ASC ) AS rownumber,* FROM student ) temp_row 
WHERE
	rownumber > (( pageIndex - 1 ) * pageSize );

-- 分页查询第2页，每页有10条记录
SELECT TOP
	10 * 
FROM
	( SELECT row_number () OVER ( ORDER BY sno ASC ) AS rownumber,* FROM student ) temp_row 
WHERE
	rownumber > 10;
```











