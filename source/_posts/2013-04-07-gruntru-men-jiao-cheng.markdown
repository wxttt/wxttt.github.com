---
layout: post
title: "Grunt入门教程"
date: 2013-04-07 11:06
comments: true
categories: ['tools', 'javascript'] 
---

这段时间在自学nodeJs,顺带的接触到了Grunt,在这里把Grunt的一些基本使用方法写出来，一来纪录自己的学习历程，二来给那些有英语阅读恐惧症的同学看，不过要深入的学习和使用Grunt,还是去[官网](http://gruntjs.com/)上看资料吧~
###什么是Grunt?
官方的说法：A Javascript Task Runner。Grunt可以用来把很多重复的任务自动化，比如js代码的压缩，合并，单元测试，检查等等，减少手动的工作，geek style~

*注意：本文只针对0.4.*版本的Grunt*


###Grunt安装
Grunt是通过npm进行安装和管理的，所以首先要确定你的电脑上安装了npm。
不知道npm是什么？自行google一下吧～

0.4.*版本的的Grunt需要nodeJs版本高于或者等于0.8.0,并且引入了一个新的元素－－－grunt-cli。

在你的项目目录中执行：
```
    npm install -g grunt-cli
```
要注意的是grunt-cli并不是grunt,他的作用是使同一台机器上可以存在不同版本的grunt，并选择离Gruntfile最近的版本运行。

安装完grunt-cli，我们需要在项目的根目录添加2个核心文件package.json和Gruntfile。

package.json文件中描述你的项目信息以及各种依赖，通过npm install可以安装其中的依赖。我们可以通过npm init来创建一个package.json文件。

Gruntfile可以是Gruntfile.js或者Gruntfile.coffee，是用来配置Grunt，安装插件以及定义任务的。

之后执行下面的命令来安装最新版本的Grunt
```
    npm install grunt-contrib-jshint --save-dev
```
使用了--save-dev参数进行安装，会在package.json文件中纪录你安装的依赖。

{% img left /images/package.png%}
####下面以jshint为例来定义一个任务
首先我们要安装jshint插件
```
npm install grunt-contrib-jshint --save-dev
```
然后编辑Gruntfile.js定义任务

{% img left /images/gruntfile.png %}

这里我在wrapper函数中做了3件事情：
```
module.exports = function(grunt) {
  // Do grunt-related things in here
};
```
1.  通过grunt.initConfig()对项目和jshint进行配置。
2.  通过grunt.loadNmpTask()载入插件。
3.  通过grunt.registerTask()定义任务。

之后我们就可以通过grunt jshint命令对src目录和src/modules下的js文件进行代码检测。

{% img left /images/jshint.png %}

###后记
Grunt是一个非常强大的工具，可以代替你做很多事情，提高你的开发效率。针对不同的用途，Grunt提供了非常多的插件，当然你也可以自己订制插件，更多详细的信息请查阅[Grunt官网](http://gruntjs.com/)



