title: Node.js小爬虫之澎湃热榜
date: 2022/09/01 10:02:00
categories:
  - 后端编程
tags: []
---

先请求下热搜榜所在页面，发现搜不到关键字
![请输入图片描述][1]

再看看开发者工具的页面链接，第一眼看请求选项卡，有个rightSidebar，进去后搜索到，说明是HTTP请求渲染上去的
![请输入图片描述][2]
![请输入图片描述][3]

Nodejs用的是Axios包,请求这个API，拿到hotNews
```javascript
var result=(await axios.get('https://www.thepaper.cn/contentapi/wwwIndex/rightSidebar',{
  headers:{
    'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 
    Chrome/104.0.5112.102 Safari/537.36 Edg/104.0.1293.70'
  }
})).data.data.hotNews
```

因为我要把这些采集的数据存到数据库，这里用到的数据库是LeanCloud，免费数据库
然后的话我用的是koa框架，支持async await语法，请求API和数据库操作都是异步
![请输入图片描述][4]

for循环里用await的话会等异步执行完才会进行下一次循环，这样才能保证采集的数据和写入数据库顺序不会混乱，那段像jQuery是用的cheerio包，可以像在客户端里一样操作DOM

还有个采集数据必不可少的就是你得让他定时采集，node-schedule包，支持cron表达式，定时每小时30分时采集一次
```schedule.scheduleJob('30 * * * *', async function(){})```


  [1]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842baa242fa0505e8f34fee269cb12273173c181fe79bb8f44b/0.png
  [2]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842baa242fa0505e8f3b176ac6aa710a07aeb4e313a0932512f/0.png
  [3]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842baa242fa0505e8f3bbf4c91c516c0765b8b169aec874ddd9/0.png
  [4]: https://p.qlogo.cn/hy_personal/3e28f14aa0516842baa242fa0505e8f36b3aa03704e229ab3292fbfb39c8c158/0.png