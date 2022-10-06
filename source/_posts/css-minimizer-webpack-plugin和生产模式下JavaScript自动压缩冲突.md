---
title: css-minimizer-webpack-plugin和生产模式下JavaScript自动压缩冲突
date: 2022/03/12 10:04:00
categories: 
  - 前端编程
tags: 
---


在production模式下webpack会自动压缩JavaScript代码，但是遇到了使用css-minimizer-webpack-plugin压缩css代码插件时自动压缩JavaScript代码失效，这个时候可以使用terser-webpack-plugin去压缩JavaScript代码，这个插件webpack5自带，不用npm安装，直接require引用就行了
