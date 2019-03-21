---
layout: page
title: About
description: 努力、奋斗
keywords: Chenquan 陈铨
comments: true
menu: 关于
permalink: /about/
---

一条有梦想、又优哉游哉的咸鱼

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
