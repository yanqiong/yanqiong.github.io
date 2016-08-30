---
layout: post
title:  "JavaScript 函数调用"
date:   2016-4-29 14:00:00 +0800
categories: javascript call apply bind
---

javascript 函数调用有 4 种模式:

+ 方法调用 
+ 正常函数调用 
+ 构造器函数调用 
+ apply/call 调用

同时，无论哪种函数调用除了你声明时定义的形参外，还会自动添加 2 个形参，分别是 this 和 arguments。

### 方法调用:

```
var a = {    
    v : 0,    
    f : function(xx) {                
        this.v = xx;    
    }
}
a.f(5);
```

### 正常函数调用

```
function f(xx) {        
    this.x = xx;
}
f(5);
```

### 构造器函数调用 

```
function a(xx){
    this.m = xx;
}
var b = new a(5);
```

构造函数一直是我认为是 js 里最坑爹的部分，因为它和 js 最初设计的基于原型的面向对象实现方式格格不入，就好像是特意为了迎合大家已经被其他基于类的面相对象实现给惯坏了的习惯。
如果你在一个函数前面带上 new 关键字来调用，那么 js 会创建一个 prototype 属性是此函数的一个新对象，同时在调用这个函数的时候，把 this 绑定到这个新对象上。当然 new 关键字也会改变 return 语句的行为，不过这里就不谈了。看代码

上面这个函数和正常调用的函数写法上没什么区别，只不过在调用的时候函数名前面加了关键字 new 罢了，这么一来，this 绑定的就不再是前面讲到的全局对象了，而是这里说的创建的新对象，所以说这种方式其实很危险，因为光看函数，你不会知道这个函数到底是准备拿来当构造函数用的，还是一般函数用的。所以我们可以看到，在 jslint 里，它会要求你写的所有构造函数，也就是一旦它发现你用了 new 关键字，那么后面那个函数的首字母必须大写，这样通过函数首字母大写的方式来区分，我个人只有一个看法：坑爹：）



### apply/call 调用

`call`, `apply`, `bind` 都是 javascript 原生函数调用方式之一.

`call`, `apply` 是即时调用, 改变了函数执行的上下文(context), `bind` 是对函数的引用.

#### call

```
function a(xx, yy) {    
    alert(xx, yy);    
    alert(this);    
    alert(arguments);
}
a.call(null, 5, 55);
```

#### apply

```
function a(xx) {        
    this.b = xx;
}
var o = {};
a.apply(o, [5]);
alert(a.b);    // undefined
alert(o.b);    // 5
```

#### bind

```
var m = {   
    "x" : 1
};
function foo(y) {
    alert(this.x + y);
}
foo.apply(m, [5]);
foo.call(m, 5);
var foo1 = foo.bind(m, 5);
foo1();
```
