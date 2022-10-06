---
title: 用async/await改变for循环promise.then()中的变量输出结果
date: 2021/10/08 16:35:00
categories: 
  - 前端编程
tags: 
  - 异步函数
  - JavaScript
---


> 这个只针对用var声明的变量，**可以用es6新增关键字 let 去声明变量就不会存在这个问题**

如果在for循环中使用promise的then方法去打印for循环的i变量会得到如下结果

![请输入图片描述][1]

可以发现控制台打印了5次i变量的值都为5，而不是0 1 2 3 4，这是因为i是全局变量，每次i++都会覆盖前一次结果，如果希望控制台能输出0 1 2 3 4这样的期望结果呢，这里就要用到async/await

![请输入图片描述][2]

async的作用就是指明loop为异步函数，await会等待promise.then()这个异步函数执行完才会继续执行for循环

  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589b2197dff61891dccba1b23aca6ac804f/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589bad93a9ba88c7790a323c8a6d9d6a3e6/0.png