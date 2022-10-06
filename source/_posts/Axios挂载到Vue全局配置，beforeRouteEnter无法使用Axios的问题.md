---
abbrlink: ''
categories:
- 前端编程
date: 2022/08/24 20:45:00
tags: []
title: Axios挂载到Vue全局配置，beforeRouteEnter无法使用Axios的问题
updated: '2022-10-06 21:05:34'
---
Vue3使用`createApp(App).config.globalProperties.axios = axios`即可把axios对象挂载到Vue实例中。

因为页面进入后再请求后台数据会有闪烁问题，即默认数据和请求数据替换
![请输入图片描述][1]
这种解决办法就是先显示个加载图标之类的，等待数据请求完成再把加载图标隐藏即可

Vue还提供了beforeRouteEnter组件路由钩子，可以在路由进入前执行一些操作，所以可以在此期间请求数据，并通过next回调的参数获取Vue实例，从而赋值数据给实例data来更新页面数据，这种方式可以完美解决闪烁问题

但由于此时无法获取Vue实例，自然Vue实例上的axios对象也拿不到

目前能想到的两种解决办法就是在使用beforeRouteEnter的组件内手动引入axios或者使用原生HTTP请求(Fetch、XMLHttpRequest)替代

```javascript
fetch('http://localhost:3000/getPosts').then(res => {
  return res.json()
}).then(res => {
  next(vm => {
    vm.posts = res
  })
})
```

[1]: https://p.qlogo.cn/hy_personal/3e28f14aa051684291d06431bce71a5c4d679c7410196d8f957939e49de5c98d/0.png
