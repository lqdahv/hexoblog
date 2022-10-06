---
title: Promise链式调用
date: 2022/02/15 01:57:00
categories: 
  - 前端编程
tags: 
---


### 链式调用

![请输入图片描述][1]

因为then方法返回的是Promise所以可以一直使用then方法获取Promise的值，为了让回调正确获取到值，可以return Promise或者其他数据类型(字符串，数组等)

但是值得注意的是，当用定时器延迟return时，下一个then方法并不会等待这个延迟执行完再调用回调函数，所以导致了最后的回调获取不到值。如果下一个回调要获取上一个延迟return值一定要return Promise

![请输入图片描述][2]

### reject终止链式调用

当进行then链式调用时，如果其中有Promise是reject（失败）的情况，那么之后的链式不会继续执行，可以用catch去捕获reject值。

![请输入图片描述][3]

Promise resolve()和Promise reject()会自动转为Promise，记得它是一个Promise对象

  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c58979dfc6eada2c05de8dc6646efc9df18f/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c5890eb84f1c5af16955145e7b99e57e1b88/0.png
  [3]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589992b2b850b7b3f1e1353c63b73523bd4/0.png