---
layout: post
title: CSS 经验
categories: CSS
description: CSS 经验
keywords: CSS
---

***男人彻底懂得一个女人之后，是不会爱她的。***

## 1、CSS 样式修改  
> 如果选中的 div 的大小或者 style 没有你要的，那就点点他周围的 div，或许有意外的发现呢  

> **<font color="#dd0000">2018-12-04 20:30</font>**  就像今晚在看一个自适应的 img，一直找不到他的大小，应该说知道大小是 width:100%，那就一定是他包围着的 div 控制的大小，如果这个 div 还看不到大小，那肯定还有一个 div 在控制着这个 div 的大小了，总着周围的 div 多点出来看看，总有意外的发现的额，第二次
犯这种错误的了  

> **<font color="#dd0000">2019-04-08 17:28</font>**  就像下午一直再看一个样式，全都看完了，就是不知道怎么居中的，结果点了上下的样式，才发现，居中的是父样式控制的，看来以后的样式主要还是要看看父样式，当前的样式没有的话，就要看看父样式了，第三次犯错了啊

> **<font color="#dd0000">2019-06-14 10:12</font>**  style="flex-grow: 1;text-align: right;"
![avatar](/images/css/20190614101501.png)  

> **<font color="#dd0000">2019-06-14 16:40</font>**  在表单里面的，偶尔使用 span 也是不错的
```html
<i-form>
    <form-item >
        <span style="font-size: 16px">积分提现：</span>
        <i-switch @on-change="editWithDrawlPointSysStatus" v-model="reportData.withDrawlPointSysStatus" size="large">
            <span slot="open">开启</span>
            <span slot="close">关闭</span>
        </i-switch>
    </form-item>
</i-form>
```

## 2、苹果 移动端 position:fixed 滑动问题
```html
<!--错误写法-->
<div style=" overflow : scroll">
     <div style="position:fixed"></div>
</div>
```
```html
<!--正确写法，应该将两个属性按照同级使用不能用包含的形式-->
 <div style="position:fixed"></div>
<div style=" overflow : scroll"></div>
```

## 3、使用 mint-ui 的上拉下滑必须使用以下属性
```html
 <div class="wrapper" style="height:100vh;overflow-y:scroll;-webkit-overflow-scrolling:touch" ></div>
```

## 4、vue 回到顶部组件
```vue
<template>
    <div class="gotoTop">
        <img class="go-top" v-if="btnFlag" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAEE0lEQVRoQ92ayUsrQRCHa9S4axT0ICqagwui4r4dBJf/2IOXJIIH44aGKOJycMeDgnvcncevoMMkmSQ9Mz2T5xQMPHyd6v66qqurakbTdV0nBfL29kZ3d3f08PBAr6+v/Hx9fdH39zdrLysro0AgQDU1Nfw0NDRQU1MTVVVVKZidSHMCkkwm6erqih8s3I4Aqq2tjZ/q6mo7Kvg3tkAeHx/p5OSEbm5ubE9s9sOWlhbq6uqiYDBoWa8lkI+PDzo4OGALuCmwTl9fH1VUVEhPIw1yfX1Ne3t77PdeCM7TwMAAtba2Sk1XEOT395f29/fp/PxcSqHqQR0dHdTf308lJSV5VecFQcTZ2triaFRMQXQbHx/nyJdLcoIAIhaLcTj9HwThenp6OieMKQjcaWNjo+iWyNxAWGZyctLUzUxBEolE0c5EIevjzAwODmYNywJBdNrZ2Smkr6j/PzIykhXN0kBwT6ysrHgWYu3uBkLz3Nxc2j2TBrK7u2vpskOeVCgsyi4W5xL5mqzg0hweHk4NT4Eg7VhdXZXVQ729vZxOqBSkPYeHh9IqZ2dnU+lMCmR7e9tS7tTT00Pd3d3Sk8oMPD4+pqOjI5mhPAa52djYGP+bQZDFRiIRaQViIHIhla6FM2pVFhYWOGtmEKs7YWUyAYoz4IYIz2CQaDRqu57It7i6ujqampriIevr6/T8/KycBfXM/Pw8aclkUg+Hw8onqK+v55SivLycdX9+ftLa2porMIuLi6RdXFzo8XhcKUgmhFAOGORvT09PSucbGhoiLZFI6GdnZ8oUo7qDO8ESOBfijPz8/FBpaSlbBm6GcK9KOjs7SYvFYvrt7a0SnchQAYGbFwtGITY6Osq6Nzc3CTsHQBRnsIwqmObmZtLC4TCHX6dihEAYxULRoEEqAcE5RD2Bc4OwDRhYRkWZwOF3eXlZd1q+NjY2cnoNSwgIRKja2to0EKQgiGRGGJQL9/f3jvYR82pLS0tOOkIECLgTdvv9/Z0t8fLywgszAxF/B0xlZSX3vWAZJzCapjkDMVZtgEB4Nfa3coGYwTipRhnEiWuhKRAKhdgSmRD5LCL8CJfZzMwMW+b09JSbHHaEXcvJYccC2tvbOfU3S8HzWUQsGKUAUvLLy0veEDvCh11l+M1chAyInYVn/obDr+oL0TiJVyB8IbqRoggYr0A4RXEraZQ57CrcCjo4aXQzjffCIqk03s3CyguQtMLKbqlbyDW8AEkrdbEgq82HQhBenJGs5gMmtdoOkgFB6jAxMcF1Cbr6qsW0HYRJrDboVC/Mir6cDToo8U3LFDC+aGIL0/ritQJgfPOiBzC+ePUmXMwXL0MFjC9eTxvj+p//YMAI44tPOIxAf/6jmswU4s9/5mSWExX7w7N/RVwpTJxVLTkAAAAASUVORK5CYII=" @click="backTop">
    </div>
</template>

<script>
    export default {
        name: "GotoTop",
        data() {
            return {
                btnFlag: false,
                scrollTop: 0,
            }
        },
        mounted () {
            window.addEventListener('scroll', this.scrollToTop, true)
        },
        destroyed () {
            window.removeEventListener('scroll', this.scrollToTop,true)
        },


        methods: {
            // 点击图片回到顶部方法，加计时器是为了过渡顺滑
            backTop () {
                const that = this
                let timer = setInterval(() => {
                    let ispeed = Math.floor(-that.scrollTop / 5)
                    let dom =document.getElementsByClassName('wrapper')[0];
                    dom.scrollTop = that.scrollTop + ispeed;
                    if (that.scrollTop === 0 || that.scrollTop === 1) {
                        clearInterval(timer)
                    }
                }, 16)
            },

            // 为了计算距离顶部的高度，当高度大于 120 显示回顶部图标，小于 120 则隐藏
            scrollToTop () {
                const that = this
                // 获取到某一个元素，然后获取他的属性值
                let dom =document.getElementsByClassName('wrapper')[0];
                let scrollTop = dom.scrollTop;

                that.scrollTop = scrollTop
                if (that.scrollTop > 120) {
                    that.btnFlag = true
                } else {
                    that.btnFlag = false
                }
            }
        }
    }
</script>

<style scoped>
    .go-top{
        position: fixed;
        bottom: 60px;
        right: 10px;
        width: 30px;
        height: 30px;
        cursor: pointer;
        background: #fff;
        border-radius: 50%;
        z-index: 99;
    }
</style>

```

## 5、document 获取滚动条的位置
```javascript
    // 获取到某一个元素，然后获取他的属性值
    let dom =document.getElementsByClassName('wrapper')[0];
    let scrollTop = dom.scrollTop;
    // 也可以直接赋值改变他的属性值
    dom.scrollTop = 0;
    
    // 这些是获取 body、等其他的大方面的 scrollTop（滚动条的位置） 
    var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;

```

## 6、document 获取全局点击属性
```javascript
    let body = document.querySelector('body')
    body.addEventListener('touchstart',(e)=>{ // 手机屏幕用的是 touchstart
        // debugger
        console.log(e.target.offsetParent.className )
        // 忽略掉原来的 div，不然会冲突，看不到效果
        if(e.target.parentElement.className != 'mobile-menu-icon' && e.target.parentElement.className != 'col-lg-6 col-md-8 col-sm-9' && e.target.offsetParent.className != 'tm-nav show'){
            // debugger
            this.tabbar = false
        }
    },false)
```

## 7、弹窗之后父窗口还会滚动
```javascript
    // 打开弹窗时修改属性
    document.getElementsByClassName('wrapper')[0].style.position = 'fixed';
    document.getElementsByClassName('wrapper')[0].style.overflow = 'hidden';

    // 关闭弹窗时修改成原来的属性
    document.getElementsByClassName('wrapper')[0].style.position = 'relative';
    document.getElementsByClassName('wrapper')[0].style.overflow = 'scroll';
```

## 8、CSS 消除 ios 点击按钮时出现的一个半透明的灰色背景
```stylus
    body{
        -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    }
```

## 9、兄弟组件通信 —— eventBus 的用法
1、新建eventBus.js
```javascript
    import Vue from 'vue'
    export default new Vue()
```
2、触发事件 —— 用来被监听
```javascript
    import eventBus from './eventBus'
    //...
    methods: {  
       addCart(event) {  
            eventBus.$emit('getTarget', event.target);   
       }  
    } 
```
3、监听事件 —— 之后调用
```javascript
   import eventBus from './eventBus'

   created () {
     eventBus.$on('getTarget', args => {
        console.log(args);  
     }) 
   }
```
记：这样，在每次【触发事件】组件的点击事件中，就会把 event.target 传递到【监听事件】中，并console出来。

## 10、ios 中 z-index 失效导致的坑
1、页面上加上 ios 的弹性滑动属性 -webkit-overflow-scrolling: touch 会导致苹果上 z-index 属性失效，安卓正常  
将弹性滑动属性的css全局样式-webkit-overflow-scrolling: touch去掉后z-index属性正常。

