---
title: javascript图片转base64
date: 2021/09/21 10:30:00
categories: 
  - 前端编程
tags: 
  - JavaScript
  - 图片处理
  - base64
---


```<input type="file" id="a" onChange="b()">```
文件上传后就会触发onChange,上传的图片文件可在获取到该dom节点后用files[0]去拿到这个图片
```javascript
var pic = document.getElementById('a').files[0]
var tobase64 = new FileReader()
tobase64.readAsDataURL(pic)
tobase64.onload = function (e) { //onload会在读取成功后触发
    console.log(e.target.result)
}
```
还有两个可能用的上的方法readAsArrayBuffer()和readAsText()
readAsArrayBuffer()返回的是arrayBuffer对象,readAsText()返回的是文本字符串，这个方法有还能接收第二个参数，指定字符串的编码类型，默认为UTF-8
[FileReade API](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader)