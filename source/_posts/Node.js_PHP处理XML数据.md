---
abbrlink: ''
categories:
- 后端编程
date: 2022/08/17 13:30:00
tags:
- node.js
- xml
title: Node.js PHP处理XML数据
updated: '2022-10-06 21:53:17'
---
> 现在XML数据相对来说比较少，微信公众号发送的信息就是XML格式的，影视采集站是json和xml

### Node.js11

[express-xml-bodyparser][1]模块会把请求体中的xml转为json格式，之后用req.body就能取到数据了

给客户端发送xml数据用[xml2js][2]模块
![nodejsxml][3]

### PHP

`file_get_contents("input://input")`方法拿到请求体源数据，拿到后再用`simplexml_load_string(xml,SimpleXMLElement,LIBXML_NOCDATA)`方法把xml转为simplexml对象，之后直接用->取值

这里有个很重要的点，如果数据中含有`<![CDATA[data...]]>`需要再传递第三个参数LIBXML_NOCDATA把CDATA数据转为字符串，没传这个参数就取不到数据

刚开始看别人文章只传了前两个参数给我整半小时，最后专门去查了这个方法才发现可以传三个参数来解决CDATA
![phpxml][4]

[1]: https://www.npmjs.com/package/express-xml-bodyparser
[2]: https://www.npmjs.com/package/xml2js#xml-builder-usage
[3]: https://i.imgtg.com/2022/08/17/Kz8jg.png
[4]: https://i.imgtg.com/2022/08/17/Kz6Rl.png
