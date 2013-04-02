---
layout: post
title: "关于浏览器模式和文档类型"
date: 2013-04-02 15:54
comments: true
categories: 
---
###关于浏览器模式
浏览器模式包括标准模式和混杂模式（quirks mode）。在标准模式中浏览器根据规范渲染页面，而在混杂模式浏览器以一种比较宽松的向后兼容的方式显示，通常会模拟老式浏览器(如IE4)的行为防止老站点无法访问。
###关于文档类型<!DOCTYPE>
<!DOCTYPE>是用来声明HTML/XHTML版本类型的，只有当浏览器知道当前文档是用什么版本来编写的，页面才会以正确的方式渲染。
####常用的声明
HTML5
```
<!DOCTYPE html>
```
HTML 4.0.1
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
```
XHTML 1.0
```
<!--过渡模式-->
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<!--严格模式-->
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" 
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!--框架模式-->
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
```
根据DOCTYPE浏览器会选择呈现模式，被称为DOCTYPE切换或者DOCTYPE侦测，当XHTML文件包含完整的DOCTYPE时浏览器会选择标准模式，当DOCTYPE不存在或者形式不正确时会导致文档以混杂模式呈现。需要注意的是DOCTYPE并不是HTML标签，但DOCTYPE声明需要是页面的第一个元素，在DOCTYPE声明之前也不要有其他多余的代码（比如编辑器自动创建的说明信息），这都可能导致文档以混杂模式呈现。  



