---
title: scroll滚动兼容性
date: 2021/12/05 00:18:00
categories: 
  - 前端编程
tags: 
  - JavaScript
  - 网页滚动
desc: 
keywords: 
sharePic: 
thumb: 
video: 
---


安卓测试的是极速浏览器(基于Chromium 73内核)国内浏览器和Chrome浏览器

分别试了两种js和一种jQuery滚动方法
```javascript
window.scroll(x,y) //window.scrollY(获取垂直滚动距离)window.scrollX(获取水平滚动距离)
document.documentElement.scrollTop = y
$('html').scrollTop = y
```
在极速浏览器中只有window.scroll(x,y)才能生效，Chrome浏览器三种方法都能用