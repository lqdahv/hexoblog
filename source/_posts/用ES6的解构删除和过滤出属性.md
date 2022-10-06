---
title: 用ES6的解构删除和过滤出属性
date: 2022/03/30 07:32:00
categories: 
  - 前端编程
tags: 
---


假如有这么个对象
```javascript
var obj={
    name:'xiaoming',
    age:80,
    position:'grass-roots',
    married:false,
    hobby:'basketball'
}
```

如想要除了married,hobby属性外的全部属性（删除）
`const {married,hobby,...all}=obj`

![删除][1]
想要married和hobby两个属性,用自执行函数来写（过滤）
```javascript
var two=(function({married,hobby}){
    return {married,hobby}
})(obj)
```

![请输入图片描述][2]
写成ES6的箭头函数就是
```javascript
var two=(({married,hobby})=> {
    return {married,hobby}
})(obj)
```

然后函数体只有一条语句时可以省略掉函数体符号{}和return，这条语句是个对象用括号括起来，最后就优化成这样了-_-
```javascript
var two=(({married,hobby}) => ({married,hobby}))(obj)
```


  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c5896f172dc7be6403977d253a298b8f6623/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842d26cd9850b43c589f6b0fc4b88a5cbd95f49a98d539620f9/0.png