---
layout: post
title: "js 对象/函数/类学习总结"
date: 2013-04-02 15:50
comments: true
categories: [js, note] 
---
##1、什么是js对象

>对象是JavaScript的基本数据类型。对象是一种复合值：他将很多值（原始值或者其他对象聚合在一起，克通过名字访问。我们可以把对象堪称是从字符串到值的映射，然而对象不仅仅是字符串到值的映射，除了可以保持自有属性。对象的方法通常是继承的属性，这种“原型式继承”是JavaScript的核心特征。（《JavaScript权威指南》）

###创建对象

```
    var obj1 = {};  //使用对象直接量
    var obj2 = new Object();  //用new创建一个空对象，和{}一样
    var obj3 = Object.create(Object.prototype); //使用ECMAScript5中的Object.create函数创建，
```
####关于原型
每一个对象（null除外）都和另外一个对象相关联这个对象，这个对象就是原型，每一个对象都要从原型继承属性。通过对象直接量创建的对象都具有同一个原型对象，可以通过Object.prototype获得该原型对象的引用。通过new关键字创建的对象的原型就是其构造函数的prototype属性值。通过new Array()创建的数组对象的原型就是Array.prototype,而通过new Object()创建出的空对象{}的原型就是Object.prototype。而Object.create()函数的第一个参数就是一个原型对象（第二个参数可选），创建出的对象的属性继承传入的原型对象。

```
    var Class = function(){
        //do some thing here
    };

    Class.prototype = {x:1,y:2};

    var obj1 = new Class() //obj1继承构造函数Class的属性prototype中的x,y
    var obj2 = Object.create(Object.prototype) //创建的是一个空对象{}
    var obj3 = Object.create({x:1,y:2}) //创建出的对象obj3继承属性x,y
```

Object.create()函数可以在通过任意原型创建新对象，换句话说就是任意对象可继承，在低版本的浏览器中可以这样模拟该函数。

```
    //inherit()返回一个继承自原型对象P的属性的新对象
    //代码来源《JavaScript权威指南》
    function inherit(p){
        if(p == null) throw TypeError();
        if(Object.create) return Object.create(p)
        var t = typeof p;
        if(t !== "object" && t!=="function") throw TypeError();
        function f(){};
        f.prototype = p;
        return new f();
    }
```

