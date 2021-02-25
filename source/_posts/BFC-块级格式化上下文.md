---
title: BFC(块级格式化上下文)
date: 2020-02-02 14:25:17
tags: CSS
---

BFC是 W3C CSS 2.1 规范中的一个概念，它的作用主要是用来清除浮动，解决margin重叠等。
<!--more-->
**BFC布局规则：**

 - 内部的Box会在垂直⽅向，⼀个接⼀个地放置。
 - Box垂直⽅向的距离由margin决定。属于同⼀个BFC的两个相邻Box的margin会发⽣重叠。
 - 每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
 - BFC的区域不会与float box重叠。
 - BFC就是⻚⾯上的⼀个隔离的独⽴容器，容器⾥⾯的⼦元素不会影响到外⾯的元素。反之也如此。
 - 计算BFC的⾼度时，浮动元素也参与计算。

  


----------


**触发BFC的条件：**

 - float不为none
 - 绝对定位元素（absolute、fixed）
 - display设置为inline-block、table-cell、table-caption、flex、inline-flex
 - overflow不为visible可看见的（hidden、scroll、auto）
 - 根元素


----------


**BFC的用处：**
	

 1. 清除浮动

	当元素被设定float属性后，它将脱离文本流，成为一个独立的容器。如果父元素没有设置宽高，
	那么由子元素撑开的空间将会消失。为父元素添加上述CSS属性触发BFC来清除浮动。当然清除
	浮动还是推荐使用after伪类和before伪类来实现。
	
	设定子元素浮动：
	{% asset_img 01.png This is an image %}
	父元素变成了一条线
	{% asset_img 03.png This is an image %}
	设定父元素overflow：hidden；
	{% asset_img 02.png This is an image %}
	父元素的空间被撑开了。
	
 2. 解决margin重叠

	在标准文档流中，块级标签之间竖直方向的margin会以大的为准，这就是margin的塌陷现象。可以用overflow：hidden产生bfc来解决。
	
	margin重叠：
	我们设置两个子元素的margin各为100px，最后需要相邻处的margin为200px。
	{% asset_img 05.png This is an image %}
	{% asset_img 04.png This is an image %}
	结果发现这两个100px的内边距重合了。想要避免重合需要将其放入两个BFC容器中。
	{% asset_img 07.png This is an image %}
	{% asset_img 06.png This is an image %}
	这时候会发现margin已经不重叠了。
	
