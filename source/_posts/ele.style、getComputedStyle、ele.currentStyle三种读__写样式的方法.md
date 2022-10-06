---
title: ele.style、getComputedStyle、ele.currentStyle三种读||写样式的方法
date: 2022/03/12 09:01:00
categories: 
  - 前端编程
tags: 
---


`ele.style`能够设置或者返回样式,但是只对内联样式(标签内style属性设置的样式)起作用
`getComputedStyle(ele,[pseudoElt]).getPropertyValue(attr)`只能获取样式，不能写入样式，**不兼容IE**
`ele.currentStyle(attr)`只能获取样式，不能写入样式，**只兼容IE**