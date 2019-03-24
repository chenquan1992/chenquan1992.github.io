---
layout: page
title: About
description: 努力、奋斗
keywords: Chenquan 陈铨
comments: true
menu: 关于
permalink: /about/
---

大丈夫当效命疆场，安内攘外，乌能龌龊久困笔砚间，自误光阴耶？

## 联系

QQ: 504996366              
WX: chequan

## 技能

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}

## 自我介绍
　　大家好，我叫陈铨，广东揭阳人，毕业于广州从化的大专院校，专业学的是机械。毕业之后从事了一年的机修工作，由于机修工作轻松，每天事情不多，所以利用了闲暇时间自学编程，在 2016 年的时候，就找了一份 java 后端开发的工作，白天上班，晚上留在公司学习，因为同事们也是刚毕业不久，所以学习氛围很好！工作了一年之后，因为待遇问题，我选择了辞职，然后就是我的上家公司，这家公司开发的是商城系统，我还是做 java 后端开发，当然晚上还是一样的，留在公司自己学习 java 知识！
