---
title: nodejs把响应内容保存到本地，而不是打开
date: 2021/10/02 19:14:00
categories: 
  - 前端编程
tags: 
  - Nodejs
  - 图片
  - 下载
---


创建一个nodejs应用时，在res.end(？)输出一个图片时，他是直接显示在网页上的，以下这个例子

![请输入图片描述][1]

我们也经常看到点击下载按钮就可以下载图片，在nodejs中想要下载保存到本地就需要向response响应中添加响应头headers，nodejs中使用response.writeHead()去添加响应头，想要做到下载功能就要把
```
res.writeHead(200,{'Content-Disposition':'attachment;filename=example.png'})
```
添加到响应头对象中。Content-Disposition有两个属性值，当你不设置Content-Disposition属性时，就是用inline作为默认值，即是上图中直接显示在浏览器中，当你设置了attachment作为属性值时，就能实现下载功能，example.png是浏览器显示的下载文件名，可自行更改为变量或常量，如下

![请输入图片描述][2]

这里补充一下，上面的例子是用http请求网络图片资源，如果要获取自己服务器磁盘上资源时可以用fs.readFile('filePath',function(ress){})方法去获取,其他代码不变，回调函数的ress参数有data事件能在读取数据时触发回调函数，参数chunk就是一段文件的Buffer数据,把data事件中获取的每段Buffer数据保存在数组中，最后用Buffer.concat()去合并，结果就是整个文件的Buffer数据了


  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589769ceea51cdcb1e97c974d42e7845675/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c58925fda2aad032d50ea8a6266dc86cb4b0/0.png