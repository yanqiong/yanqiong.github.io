---
layout: post
title:  "JavaScript 类型判断"
date:   2016-4-29 14:00:00 +0800
categories: javascript call apply bind
---

### javascript 基本类型

undefined, null, bool, number, string, object 和 function

Number, String, Object, Function 等是 JavaScript 的内置函数


### typeof
 返回值只有 undefined string number boolean object function

```
typeof 12312.23  //"number"
typeof "nihao"  //"string"
typeof undefined  //"undefined"
typeof true  //"boolean"
typeof null  //"object"
typeof setInterval   //"function"
```


### instanceof

```
var s = new Number(234);
s instanceof Number; //true
```

### Object.prototy.call()



###
