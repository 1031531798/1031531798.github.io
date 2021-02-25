---
title: call和apply方法使用
date: 2020-01-20 12:32:55
tags: JavaScript
---

# 1. apply方法

 -  apply:方法能劫持另外一个对象的方法，继承另外一个对象的属性.就是重新定位this。

 -  apply的用法： apply(obj,arguments) 。接受两个参数 obj 是指定的this对象 ， arguments 是指传递的参数。
 -  下面看一组案例：
<!--more-->
```
	function person(name, age, sex) {
		this.name = name;
		this.age = age;
		this.sex = sex;
		console.log("姓名：" + this.name + " 年龄：" + this.age + " 性别：" + this.sex)
	}
	var arr = ['林','20','男']
	function staff(name, age, sex) {
		person.apply(this,arr)
	}
	staff() //打印 姓名：林 年龄：20 性别：男
```
函数staff 没有定义属性，也没有定义打印。而所有方法通过apply劫持了person函数的方法。

这里我传递的是一个数组，但是apply接受的是一个参数，因为apply可以将一个数组默认的

转换为一个参数列表。

# 2. call方法

call方法和apply方法类似，都是重新定义this的指向。
区别在于call的参数是一个个定义的；apply的参数是一个数组形式。
如果你用call方法传入一个数组
	
	
``` 
	function person(name, age, sex) {
		this.name = name;
		this.age = age;
		this.sex = sex;
		console.log("姓名：" + this.name + " 年龄：" + this.age + " 性别：" + this.sex)
	}

	function staff() {
		person.call(this, ['lin', "20", "nan"])
	}
	 staff() //姓名：lin,20,nan 年龄：undefined 性别：undefined
```

  结果就是将数组变成一个参数的值。
  

 - 所有如果你传递参数的时候适合数组，那你就可以用apply方法。

  

 - 如果用数组不方便就可以用call方法。

  方法是死的 ，怎么组合方法，活用方法，才能更好解决问题。
  
  本文参考自https://www.cnblogs.com/chenhuichao/p/8493095.html
  如有不足，请多多关照！