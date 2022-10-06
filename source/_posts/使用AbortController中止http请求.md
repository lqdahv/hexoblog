---
title: 使用AbortController中止http请求
date: 2022/08/08 23:51:00
categories: 
  - 前端编程
tags: 
---


AbortController可以中止Fetch请求，在Axios的0.22.0版本后也可以使用该方法。
```javascript
var controller=new AbortController()
var signal=controller.signal
function mydata(){
  fetch('/api',{signal:signal}).then()
} 
```
使用`controller.abort()`即可中止存在`{signal:signal}`信号的请求

### 存在的问题
当第二次使用该请求时会发现无法再次发送请求，这个问题的原因是controller.abort()中止请求后[signal的aborted属性就为true](https://developer.mozilla.org/zh-CN/docs/Web/API/AbortSignal)(表示已中止了请求)，导致了无法再次发送请求，所以解决办法就是把用过的AbortController实例清空重新创建新实例
```javascript
  var controller=null
  var signal=null
  function mydata(){
    controller=new AbortController()
    signal=controller.signal
    fetch('/api',{signal:signal}).then()
  } 
  function abort(){
    if(controller){
      controller.abort()
      controller=null
    }
  } 
```
上面代码abort中止函数会判断是否有AbortController实例controller，如果有就中止它并且清空中止后的实例，在下次请求时会创建一个新实例，拿到的就是新的signal，就不会存在无法发送请求的情况

