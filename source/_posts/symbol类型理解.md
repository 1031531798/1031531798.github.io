---
title: symbol类型理解
date: 2020-02-22 16:06:19
tags: [ES6,Javascript] 
---

Symbol类型是ES6新增的基础数据类型，可以调用symbol（）函数来创建一个symbol实例。<!--more-->
``` javascript
let sym = Symbol()
```

你可以在symbol函数中添加一个参数，用来描述信息：
``` javascript
let sym = Symbol('another symbol')
```
用TypeScript的方式来描述这个Symbol()函数的话，可以表示成：

``` javascript
function Symbol(description?: any): symbol
```

****symbol的特点****

 - **每一个实例都是唯一的，因此比较两个实例时会返回false。**
	![Loading failed](01.png)
	![Loading failed](02.png)
 
 - **Symbol定义的属性未被包含在对象自身的属性名集合(property names)之中，所以在for in 或者 keys()枚举时，无法枚举出symbol类型的key。**
 
	![Loading failed](03.png)
	如果要获取symbol类型的对象属性，可以用一些专门针对Symbol的API：

	![Loading failed](01.png)
另外在模块中经常会使用Symbol定义类的私有属性/方法，由于symbol是唯一的，只能在定义文件中查看到。外部文件无法访问到symbol类型的对象属性。

参考：https://www.jianshu.com/p/f40a77bbd74e