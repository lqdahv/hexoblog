---
title: file-loader,url-loader在webpack5中废弃，改用asset module
date: 2022/03/06 01:46:00
categories: 
  - 前端编程
tags: 
---


之前版本file-loader,url-loader能够处理输出css样式中的图片和字体文件，webpack5已经可以使用内建的资源模块类型(asset module type)，html中的img标签图片还需要使用html-loader。
资源模块类型可以规定以下4种type属性值
type: asset/resource 之前版本的 file-loader 功能
type: asset/inline   之前版本的url-loader 输出为base64编码
type: asset/source   之前版本的raw-loader 导出源代码
type: asset   之前版本的url-loader 这个可以规定小于多少kb时输出base64编码

自定义输出文件名
```javascript
generator: {
    filename: '[hash:6][ext][query]'
}
```
或者在output对象添加assetModuleFilename: 'images/[hash][ext][query]

url-loader能在小于规定kb时自动把图片转为base64编码，现在使用以下实现
```javascript
parser:{
    dataUrlCondition:{
        maxSize: 8*1024
    }
}
```
如果想继续用这些loader可以添加type: 'javascript/auto'属性值