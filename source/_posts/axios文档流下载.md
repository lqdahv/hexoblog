---
title: axios文档流下载
date: 2021/07/15 09:18:00
categories: 
  - 前端编程
tags: 
  - axios
  - HTTP
---


```javascript
axios({
    method: 'post',
    url:**, //要下载的文件链接
    responseType: 'arraybuffer'
}).then((data) => {
    var url = window.URL.createObjectURL(new Blob([data.data], { type: 'arraybuffer' })) 
    //创建a链接 并设置隐藏 模拟click()方法点击 
    const link = document.createElement('a')
    const text = document.createTextNode('下载图片')
    link.appendChild(text)
    link.style.display = 'none'
    link.setAttribute('download', '1280.jpg') //设置下载名称 
    link.href = url
    document.body.appendChild(link)
    link.click()
    window.URL.revokeObjectURL(url)
    document.body.removeChild(link)
})
```