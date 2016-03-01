---
layout: post
title: "手机浏览器触摸事件"
date: 2016-03-01 11:38:53 +0800
description: "关于click事件与touch事件冲突的问题 "
category: 
tags: []
---

## 关于click事件与touch事件冲突的问题

{% highlight javascript %}
var flag = false;
var $selector = $('#selectorID');

$selector.on('touchstart touchmove touchend', function(event) {

switch(event.type) {
    case 'touchstart':
        falg = false;
        break;
    case 'touchmove':
        falg = true;
         break;
    case 'touchend':
        if( !falg ) {
            console.log('点击');
        } else {
            console.log('滑动');
        }
        break;
}
});
{% endhighlight json %}

