---
layout: post
title: 安卓 helloword 第一次编译
categories: 安卓
description: 安卓 helloword 第一次编译
keywords: 安卓 helloword 第一次编译
---

## 第一次编译需要修改配置：
1、转载：https://blog.csdn.net/J6wuli/article/details/90718471
```java
// Top-level build file where you can add configuration options common to all sub-projects/modules.

buildscript {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/repositories/central/'}
        google()
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.2'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        maven{ url 'http://maven.aliyun.com/nexus/content/repositories/central/'}
        google()
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```
