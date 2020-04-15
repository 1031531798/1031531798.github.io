---
title: ES6语法简介
date: 2020-02-27 18:07:35
tags: javascript
---
## ES6简介
ECMAScript 6（以下简称ES6）是JavaScript语言的下一代标准。本文将简单讲解下ES6语法的特性。

首先介绍下几个最常用的ES6特性：
<!--more-->
 **1. let**
 	`let ` 和 `var `一样是用来声明变量的。区别是`let `声明的变量只能在声明的块级作用域内获取到，而且不同于`var`的变量提升，`let`会带来一个暂时性死区，也就是在没有`let`声明变量之前想获取这个变量，就会报错，不同于`var`变量提示所显示的undefined。
	
暂时性死区
``` javascript
	function obj(){
				console.log(bb) //undefined
				console.log(aa) //报错
				let aa = 10;
				var bb = 12;
			}
			obj()
```
变量作用域

```javascript
	var arr = [];
		for(var i = 0;i < 10;i++){
			arr[i] = function(){
				console.log(i)
			}
		}
		arr[3]()// 10
		var arr2 = [];
		for(let i = 0;i < 10;i++){
			arr2[i] = function(){
				console.log(i)
			}
		}
		arr2[3]()// 3
```
由于`var` 的作用域是全局的，所以var 声明的变量的值都是10。而`let`每个变量只在声明的作用域中有效，就避免了变量泄露。

 **2. const**

`const`用来定义常量，一旦声明，变量的值就不能改变，否则将会报错。

```  javascript
			const book = 300;
			book = 120; //报错：TypeError: Assignment to constant variable.
```
 **3. class，extends，super**
class，extends，super是ES6中非常有用的特性，它们涉及到了ES5中非常复杂的几个部分：原型，继承和构造函数。新的class写法让对象原型的写法更加清晰、更像面向对象编程的语法，也更加通俗易懂。下面直接看代码：

``` javascript
	class pro{
				constructor(name,age,sex,job) {
				    	this.name = name;
					this.age = age;
					this.sex = sex;
					this.job = job;
				}
				show(text){
					console.log(text + "," + this.name)
				}
			}
			let lin = new pro("linzijian",22,"男","web前端");
			let dong = new pro("dongbiyao",21,"男","设计员");
			console.log(lin)//{name: "linzijian", age: 22, sex: "男", job: "web前端"}
			console.log(dong)//{name: "dongbiyao", age: 21, sex: "男", job: "设计员"}
			lin.show("good");//good,linzijian
			dong.show("hellow");//hellow,dongbiyao
```
通过`class`关键词定义一个类，必须声明一个`constructor `构造函数，这个构造函数内定义的属性和方法只有该实例才能获取，是其独有的属性和方法，而下面的`show `方法则可以通过继承让别的对象使用。通过`new` 关键词引用类来创建对象。建立的对象拥有`pro`实例的所有属性和方法。

接下来看一个类的继承：

``` javascript
	class book extends pro{
				constructor(name,price){
					super();
					this.name = name;
					this.price = price;
				}
			}
			let books = new book("锋利的jQuery",80)
			console.log(books.age)//undefined
			books.show("nice")// nice,锋利的jQuery
```
上面的代码我们继承了之前的`pro `实例，子类只能继承父类公共的方法和属性-—— `show() `。同时要注意子类必须在`constructor `构造函数中使用`super() `方法，否则会报错。因为子类没有自己的 `this `对象，所以需要先通过`super() `方法引用父类的`this `对象，在由子类的构造函数重新修改`this `。

 **4. arrow:箭头函数**
 
 箭头函数在ES6中被相当多得用到，它的用法非常简单
 `(i)=>{ return i+10 } ` 等价于 `function (i){ return i+10 } `
 除了简洁的写法，箭头函数还有改变`this `指向的强大功能。
 

``` javascript
	class pro{
				constructor(name,age,sex,job) {
				    this.name = name;
					this.age = age;
					this.sex = sex;
					this.job = job;
				}
				show(text){
					console.log(text + "," + this.name)
				}
				myJob(){
					setTimeout(function(){
						console.log("我的工作是" + this.job)
					},1000)
				}
			}
			let lin = new pro("linzijian",22,"男","web前端");
			lin.myJob()//我的工作是undefined
```
在上面的代码中由于`setTimeout`方法的`this`是指向全局对象的，所以获取不到。

使用箭头函数：

``` javascript
	class pro{
				constructor(name,age,sex,job) {
				    this.name = name;
					this.age = age;
					this.sex = sex;
					this.job = job;
				}
				show(text){
					console.log(text + "," + this.name)
				}
				myJob(){
					setTimeout(()=>{
						console.log("我的工作是" + this.job)
					},1000)
				}
			}
			let lin = new pro("linzijian",22,"男","web前端");
			lin.myJob()//我的工作是web前端
```
箭头函数将改变this指向，原因是因为箭头函数是没有自己的this，它的this就是外层代码块的this。

 **4. default和rest**
 在设置函数参数的时候，default特性能设置不传递参数时候的默认值。rest特性代表不定参数，可以支持传递多个参数。看下方代码：
 
 
 传统方法设置参数默认值
 

``` javascript
	function no1 (type){
				type = type||"类型"
				console.log(type)
			}
			no1()//"类型"
```
default设定默认值、

``` javascript
	function no1 (type="type"){
				console.log(type)
			}
			no1()//类型
```
rest设定不定参数：

```javascript
	function no1 (...type){
				console.log(type)
			}
			no1("类型1","类型2","类型3")//["类型1", "类型2", "类型3"]
```
以上就是ES6比较常用的语法，相比ES5，ES6的语法相对简洁，清晰。

本文参考知乎作者Kiven666
