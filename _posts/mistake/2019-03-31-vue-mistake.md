---
layout: post
title: Vue
categories: 犯错记录
description: Vue犯错
keywords: Vue犯错
---

没有一个女子是因为她的灵魂美丽而被爱的。

## 越墙
1、components 犯错，复制的代码中出现两次 components 导致只使用了晚运行的 components，从而出现引入的组件一直不存在  
切记：以后对于复制的代码，特别注意关键词不能重复，例如 method、created 等等！
```
export default {
  components: {
    Actionsheet
  }
}
```


