---
title: Vue路由传参的三种方式
date: 2021/08/27 09:04:00
categories: 
  - 前端编程
tags: 
  - Vue路由
  - Vue传参
---


路由:从一个页面导航到另一个页面，可以传参数到新页面，有三种方式

当用router-link标签进行跳转时(声明式导航)，路由文件的path值用<font color="red">:prop</font>(prop名字随意)去接收路由链接的参数，用this.$route.params.<font color="red">prop</font>就能拿到传过来的参数注意

![请输入图片描述][1]
![请输入图片描述][2]
![请输入图片描述][3]
![请输入图片描述][4]
--- 

还有两种是通过绑定to属性，这种方式在路由文件的**path就不用写:prop去接收了,记得去掉**

**:to{path:'about',query:{prop:'参数参数'}}**

![请输入图片描述][5]
用this.$route.query.prop去获取参数

![请输入图片描述][6]
浏览器地址栏里会出现?prop=参数参数

--- 
**:to{name:'About',params:{prop:'命名路由的参数'}}**
路由文件里要写上name:About，不然会找不到这个路由

![请输入图片描述][7]
用this.$route.params.prop去获取参数

![请输入图片描述][8]

这种方式地址栏不会出现参数，而且当刷新网页时参数会丢失

这两种方式在编程式导航里效果是一样的
this.$router.push({path:'about',query:{prop:'参数参数'}})
this.$router.push({name:'About',params:{prop:'命名路由的参数'}})

  [1]: https://img10.360buyimg.com/ddimg/jfs/t1/206967/33/7152/44163/617b41b7E34fbd586/a129c5b48eb45946.png
  [2]: https://img13.360buyimg.com/ddimg/jfs/t1/203659/32/13099/50428/617b41d9E5a321cd6/28f80768eab8e2f6.png
  [3]: https://img13.360buyimg.com/ddimg/jfs/t1/207973/18/7221/44875/617b41edE23302fd2/acd17d1259733e48.png
  [4]: https://img11.360buyimg.com/ddimg/jfs/t1/161548/8/22787/10466/617b4622E0b971619/b41ef058ed862b03.png
  [5]: https://img10.360buyimg.com/ddimg/jfs/t1/170217/33/21283/41772/617b4779E6ec216cd/5e6fae57dd89e5b4.png
  [6]: https://img12.360buyimg.com/ddimg/jfs/t1/219012/19/2250/8813/617b4622E565a5b79/422be182c93361ff.png
  [7]: https://img14.360buyimg.com/ddimg/jfs/t1/141331/36/21084/40940/617b4841E9b60f188/f1e918dc233fdece.png
  [8]: https://img13.360buyimg.com/ddimg/jfs/t1/145941/14/21202/11374/617b4841E157d8ebc/f3aa6bf430628165.png