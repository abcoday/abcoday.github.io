---
layout: post
title: "正则表达式资料"
date: 2016-05-30 14:21:23 +0800
description: ""
category: 
tags: []
---

## [正则基础之——NFA引擎匹配原理](http://blog.csdn.net/lxcnn/article/details/4304651)

为什么要了解引擎匹配原理
一个个音符杂乱无章的组合在一起，弹奏出的或许就是噪音，同样的音符经过作曲家的手，就可以谱出非常动听的乐曲，一个演奏者同样可以照着乐谱奏出动听的乐曲，但他/她或许不知道该如何去改变音符的组合，使得乐曲更动听。
作为正则的使用者也一样，不懂正则引擎原理的情况下，同样可以写出满足需求的正则，但是不知道原理，却很难写出高效且没有隐患的正则。所以对于经常使用正则，或是有兴趣深入学习正则的人，还是有必要了解一下正则引擎的匹配原理的。