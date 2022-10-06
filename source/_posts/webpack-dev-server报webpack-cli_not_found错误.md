---
title: webpack-dev-server报webpack-cli not found错误
date: 2022/03/06 03:11:00
categories: 
  - 前端编程
tags: 
---


webpack-dev-server4.0.0之前用npx webpack-dev-server启动本地服务器，webpack>=4.0.0后用这个命令会报webpack-cli not found,需要用webpack serve来启动server服务,并且static属性来提供服务路径