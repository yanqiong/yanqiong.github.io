---
layout: post
title:  "JavaScript 一些函数"
date:   2016-5-20 00:00:00 +0800
categories: JavaScript 学习笔记
---

动态加载 js

```
function loadScript(url, callback) {
    var head = document.getElementsByTagName('head')[0];
    var script = document.createElement('script');
    script.type = 'text/javascript';
    script.src = url;
    script.onload = callback;
    head.appendChild(script);
  }
```

```
var s = [1,2,3,4,5,6];
s.splice(0,3); //[1, 2, 3]
s; //[4, 5, 6]

var s = [1,2,3,4,5,6];
s.slice(0,2); //[1, 2]
s; //[1, 2, 3, 4, 5, 6]
```

### 深复制 浅复制
 
 
#### 复制数组

##### 1 by slice

```
var arr = [1, 2, 3];
var copyArr = arr.slice(); 
copyArr.push(4); // 4
console.log(copyArr); // [1, 2, 3, 4]
console.log(arr); // [1, 2, 3]
```

##### 2 by concat

```
var arr = [1, 2, 3], copyArr; 
copyArr = arr.concat(); 
```

##### 3 by loop

```
var newArr = []; 
        for (var i=0, j=arr.length; i<j; i++) { 
            newArr.push(arr[i]); 
        } 
        return newArr; 
```

##### 4 针对 **对象/数组**, 先序列化再解析字符串

```
function copy( obj ){
    return JSON.parse( JSON.stringify( obj ) );
}
var data = { name: "neekey", sex: "male" }
var dataCopy = copy( data );
```