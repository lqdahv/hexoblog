---
title: 解决中文input输入事件在pc端触发两次
date: 2022/05/13 07:55:00
categories: 
  - 前端编程
tags: 
---


电脑输入法为中文时input事件会触发两次，在手机端是正常的，可以用`compositionend`事件替代input解决这个中文输入问题，但是除了中文外的数字，字符等都不会触发这个事件。
`console.log`打印触发两次的时间间隔只相差1毫秒，所以可以把最后那次触发的给剔除掉
这里可以用[防抖或者节流][1]都能达到目的，防抖节流的时间设置在1毫秒后就能剔除掉第二次触发事件


  [1]: /archives/10.html