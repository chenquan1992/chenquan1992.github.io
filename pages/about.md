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
