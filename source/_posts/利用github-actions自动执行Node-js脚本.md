title: 利用github actions自动执行Node.js脚本
tags: []
categories:
  - 后端编程
date: '2022-09-21T20:16:50.000Z'
---
> 上一篇爬取澎湃热榜里说到node-schedule定时任务，但在白嫖Vercel无服务函数时并不会执行这个包，无奈只能另想它法

这里使用**免费**的github actions

首先在仓库下新建文件```.github/workflows/abc.yml```,文件名随便取

```yml
name: coupons //自定义
on:
  schedule:   
    - cron: '5 7-23 * * *' //cron表达式，用于将任务放置队列
  workflow_dispatch: //定义这个可以手动执行，否者不会显示手动执行按钮
jobs:
  run-coupons: //这个也可以自定义，只是显示
    runs-on: ubuntu-latest //运行在最新ubuntu
    steps: // 这个就是执行步骤
      - uses: actions/checkout@master
      - name: Setup Node.js
        uses: actions/setup-node@v2 //设置运行时的nodejs环境
        with:
          node-version: '16' // 16版本的nodejs
      - name: Install Dependency       
        run:
          npm install axios //不push node_modules就要安装
          node ./index.js //运行根目录index.js文件
```

在本地push到仓库时，如果不```push node_modules```模块文件夹，那就需要在添加```npm install 模块名```,比如index.js要用到axios，那就```npm install axios```去安装。还有```push package.json```，那么只需要```npm install```就会安装全部依赖

重要的提示一下，设置的cron表达式并不是说设置了 ```0 * * * *```就会每小时0分执行脚本，它只是把执行放入队列，真正执行可能时稍后几分钟，或者不会执行，想精确定时任务这种是达不到要求的