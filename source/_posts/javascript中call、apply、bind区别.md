---
title: javascript中call、apply、bind区别
date: 2018-07-11 16:31:18
tags: js
---

call、apply、bind 三个方法都是用来改变方法中 this 的指向的
只是在使用的方式上有所区别。

call 改变 this 的指向的同时直接调用该方法。

apply、bind 只会改变方法的 this 指向，不会直接调用该方法，只是两者的传参方式略有不同。

他们俩之间的差别在于参数的区别，call 和 apply 的第一个参数都是要改变上下文的对象，而 call 从第二个参数开始以参数列表的形式展现，apply 则是把除了改变上下文对象的参数放在一个数组里面作为它的第二个参数。
