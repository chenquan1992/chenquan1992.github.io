---
layout: post
title: Vue 使用 Fontawesome 的步骤
categories: Vue
description: Vue 使用 Fontawesome 的方法
keywords: Vue Fontawesome
---

***我爱你，关你什么事？千怪万怪也怪不到你身上去。***

## 1、[Fontawesome Github 地址](https://github.com/FortAwesome/vue-fontawesome#get-started)
## 2、[Fontawesome 搜索图标地址](https://fontawesome.com/icons?d=gallery&m=free)

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
        <!--第一种写法-->
       <font-awesome-icon icon="user-secret" />
       <font-awesome-icon icon="address-book" />
       <font-awesome-icon icon="address-card" />
       <!--第二种写法：fas、fab 是前缀，省略了 fa-->
        <font-awesome-icon :icon="['fas','address-card']"/>  
        <font-awesome-icon :icon="['fab','weixin']"/>
        <i class="fas fa-address-book"></i> <!--案例，需要改写-->
  </div>
</template>
```
```vuejs
// 两种不同的库
import { faUserSecret,faAddressBook,faAddressCard } from '@fortawesome/free-solid-svg-icons'
import { faWeixin } from '@fortawesome/free-brands-svg-icons'           

import { library } from '@fortawesome/fontawesome-svg-core'

// 都必须要 library 才能使用
library.add(faUserSecret,faAddressBook,faAddressCard,faWeixin)
```

4、小记  
答：搜索得来的样式是 ```<i class="fas fa-address-book"></i>```，这时候 fa-address-book 改为驼峰型，即：faAddressBook  
import { faAddressBook } from '@fortawesome/free-solid-svg-icons'  
library.add(faAddressBook)  
<font-awesome-icon icon="address-book" />  
这样就可以使用，一共三个步骤    