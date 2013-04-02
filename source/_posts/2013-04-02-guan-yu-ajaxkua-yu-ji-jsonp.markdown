---
layout: post
title: "关于Ajax跨域及JSONP"
date: 2013-04-02 15:55
comments: true
categories: [js, ajax, JSONP, note] 
---
##1、什么是Ajax
Ajax是Asynchronous JavaScript and Xml(异步的Javascript和XML技术)的缩写，是一套综合了多项技术的浏览器开发技术。
具体的说来则包括

*   用XHTML+CSS来表达信息；
*   用JavaScript来操作DOM来实现动态效果；
*   运用XML，XSTL，JSON等操作数据；
*   运用XmlHttpRequest在客户端和服务器进行异步数据交换；
*   运用JavaScript技术来实现

通俗的讲通过Ajax，我们可以在不更新整个页面的情况下，在浏览器和服务器之间进行数据交换，并在页面中发生响应，实现页面的动态更新。

##2、Ajax跨域问题
由于JavaScript的同源策略，XmlHttpRequest对象生成的Http请求到脚本所属文档的web服务器，这就导致Ajax在进行跨域数据请求时会遇到问题,请求失败。
1.  比如aaa.somesite.com中的脚本要访问bbb.somesite.com中的文档
2.  比如siteA.com中的脚本要访问siteB.com中的文档

解决方法：

1.  对于aaa.somesite.com和bbb.somesite.com这种情况，可以在各自的脚本中修改Document对象中的domain属性为一致的somesite.com，这样这两个文档就有了同源性。
2. 在服务器中设置Access-Control-Allow-Origin响应头，比如siteA.com想somesiteB.com/content发送跨域请求(以nodeJs/express为例)

```
    app.all('/content',function(req,res){
        res.header("Access-Control-Allow-Origin", "*");
        //...
    })
```
3、在服务器中进行代理，用服务器向其他域请求数据，然后渲染在本域的页面中，这样本域的其他页面就可以通过同域通信间接获得其他域的数据，当然这样的会牺牲掉一部分性能。
4、html5标准中的postMessage()方法。

推荐一款跨域神器：[easyxdm](http://easyxdm.net/)

##3、关于JSONP
在很多地方JSONP都被描述成Ajax的一种，像Jquery中也把JSONP封装成Ajax的样子，但事实上JSONP他既不是JSON也不是Ajax,他是利用script不受同源策略限制的特性来进行跨域数据通信的一种方式。  
 
详细的讲解见[说说JSON和JSONP，也许你会豁然开朗，含jQuery用例](http://www.cnblogs.com/dowinning/archive/2012/04/19/json-jsonp-jquery.html)
