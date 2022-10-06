---
title: vuejs标签/选项卡切换效果
date: 2021/09/08 20:38:00
categories: 
  - 前端编程
tags: 
  - Vue
---


相信有看到过很多这种常用的效果，切换上面不同的按钮显示不同内容，vuejs可以很容易实现这种效果

![请输入图片描述][1]

在vuejs中有一个component标签，这个标签有个is属性，通过v-bind绑定这个属性就可以切换不同的组件，下面写了个例子

![请输入图片描述][2]

引入两个组件tabOne和tabTwo并注册，component标签绑定的is属性值在data()中通过tab来改值，然后通过one和two两个函数改变tab的值，值就是组件名称，点击两个按钮后就会发现显示的是两个不同组件了

![请输入图片描述][3]

这里也出现另一种情况，切换回来的时候输入框里面的内容没了？在切换不同组件时都是新创建实例的，所以会出现组件默认状态，input是默认没输入的，123是我自己输入的，所以切换回去输入框为空。
如果想保留切换之前的状态，可以使用keep-alive缓存标签

![请输入图片描述][4]


  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c5899afa74b875bc5305588db695769807bc/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c5892514c0c3b4cd77014db22648520f17ba/0.png
  [3]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589ac6dedcec008fd6db0d835246583ff00/0.png
  [4]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589c0e487c71c0f24a1d289cf83ae39542c/0.png