---
layout: post
title: Vue 使用 Fontawesome 的步骤
categories: Vue
description: Vue 使用 Fontawesome 的方法
keywords: Vue Fontawesome
---

***我爱你，关你什么事？千怪万怪也怪不到你身上去。***

1、先安装
```
$ npm i --save @fortawesome/fontawesome-svg-core
$ npm i --save @fortawesome/free-solid-svg-icons
$ npm i --save @fortawesome/vue-fontawesome

$ npm i --save @fortawesome/free-brands-svg-icons
$ npm i --save @fortawesome/free-regular-svg-icons

npm 的过程可能需要翻墙才能安装成功
```

2、src/main.js 下配置
```
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
Vue.component('font-awesome-icon', FontAwesomeIcon)
```

3、使用
```vue
<template>
  <div id="app">
       <font-awesome-icon icon="user-secret" />
       <font-awesome-icon icon="address-book" />
       <font-awesome-icon icon="address-card" />
  </div>
</template>
```
```vuejs
import { faUserSecret,faAddressBook,faAddressCard } from '@fortawesome/free-solid-svg-icons'
import { library } from '@fortawesome/fontawesome-svg-core'

library.add(faUserSecret)
library.add(faAddressBook)
library.add(faAddressCard)
```