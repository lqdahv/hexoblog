---
title: 数组的map()方法对数组里对象的合并处理
date: 2021/11/22 09:50:00
categories: 
  - 前端编程
tags: 
  - JavaScript
  - js数组处理
  - 数组过滤
---


假设有以下两个数组
![](https://cdn.jsdelivr.net/gh/lqdahv2/blogImg/typecho/map方法合并1.png)
两个数组中都有name属性值为小明的对象，第二个数组中多了一个QQ的属性，现在想把这个QQ合并到第一个数组中，可以使用**map()**方法进行合并处理

![](https://cdn.jsdelivr.net/gh/lqdahv2/blogImg/typecho/map方法合并2.png)
map()其实也是循环方法，item1为当前循环的数组元素，也就是里面的对象。首先用filter去过滤出arr2中是否包含当前item1的name相同的对象，如果找到(**filter.length!=0**)就能把第二个数组中过滤出的对象属性赋值给第一个数组的当前对象属性(**item1.QQ=filter[0].QQ**),然后return这个item1，**如果不进行return，那返回的是undefined,所以记得一定要返回。**
还有如果第二个数组的小明对象有很多个属性，想把里面的属性全部合并给第一个数组，那可以用ES6对象方法**Object.assign(to,from)**去合并两个对象，相同属性的话后面属性会覆盖前面属性