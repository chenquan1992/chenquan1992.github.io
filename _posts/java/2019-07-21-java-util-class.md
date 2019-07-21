---
layout: post_two
title: Java 基础工具类 
categories: Java基础
description: 基础工具类
keywords: 基础工具类
---

***爱上一个人的时候，总会有点害怕，怕得到他；怕失掉他。***

### 1、Mybatis打印可执行mysql语句(工具和拦截器两种方式)  
切记：以后对于复制的代码，特别注意关键词不能重复，例如 method、created 等等！
```java
public class MybatisSqlGenerator {

    public static void main(String[] args) {
        String sqlNew = "";
        String sqlNoParamString = "";
        String paramString = "";

        sqlNoParamString = "SELECT * from test where param1=? and param2=?";
        paramString = "1(Integer), 2(String)";

        String[] sqlArray = sqlNoParamString.trim().split("[?]");//如果sql语句最后一个为？数组和没有？是一样的结果
        String[] paramArray = paramString.split(",");
        String paramType = "integer";//integer string
        int count = sqlArray.length;
        for (int i = 0; i < count; i++) {
            sqlNew += sqlArray[i];
            if (i == (count - 1) && !sqlNoParamString.trim().endsWith("?")) {//如果最后一个？不在末尾，则已经没有参数了
                break;
            }
            if (paramArray[i].trim().equals("null")) {//null操作
                sqlNew = sqlNew + paramArray[i];
                continue;
            }
            paramType = paramArray[i].substring(paramArray[i].indexOf('(') + 1, paramArray[i].indexOf(')')).toLowerCase();
            if (paramType.equals("string")) {
                sqlNew = sqlNew + "'" + paramArray[i].substring(0, paramArray[i].indexOf('(')).trim() + "'";
            } else {
                sqlNew = sqlNew + paramArray[i].substring(0, paramArray[i].indexOf('('));
            }
        }
        System.out.println(sqlNew);
    }

}
```


