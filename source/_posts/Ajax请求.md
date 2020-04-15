---
title: Ajax请求
date: 2020-01-23 20:26:05
tags: javascript
---

###### 1.什么是Ajax

Ajax 即“Asynchronous Javascript And XML”（异步 JavaScript 和 XML），是指一种创建交互式、快速动态网页应用的网页开发技术，无需重新加载整个网页的情况下，能够更新部分网页的技术。<!--more-->

在以前浏览器向服务器发送请求会导致用户不能操作和刷新网页，使用Ajax请求可以异步获取服务器的响应，从而优化用户交互体验。

Ajax并不是一种编程或脚本语言，它只是一种相互关联的技术，用于异步发送服务器请求。

###### 2.Ajax原理
Ajax就是在浏览器向服务器发送请求的过程中，可以进行别的操作，而不需要在服务器响应之前一直处于等待状态，不能进行页面的操作。Ajax的==XMLHttpRequest #F44336==对象就是用来连接浏览器与服务器，使得浏览器可以不用一直等待服务器的响应。
首先需要创建一个==XMLHttpRequest #F44336==对象
``` javascript
 var xhr = new XMLHttpRequest();
```
有了XML对象我们就需要设置传输数据的形式，Ajax有两种方法：GET和POST。
==open==方法创建一个新的http请求，并指定此请求的方法、URL以及验证信息。`

``` javascript
xhr.open('POST', 'api/login/userLogin', true);
```
介绍下比较重要的三个参数，第一个为请求的类型，第二个是URL地址，第三个为指定此请求是否为异步方式，默认为true。如果为真，当状态改变时会调用onreadystatechange属性指定的回调函数。

``` javascript
 xhr.send(new FormData($("#login_form")[0]));
 ```
 最后通过==send==方法像服务器发送数据。服务器返回的状态码可以用`xhr.onreadystatechange`监听状态码的变化。然后通过`xhr.readyState`获取状态码。
 
这是原生的Ajax使用方法，下面介绍下jQuery的Ajax使用方法：

``` javascript
$.ajax({
                type: "POST",
                url: "api/regist",
                data: data,
                dataType: "json",
                contentType: "application/json",
                success: function (data) {
                    window.location.href = "login.html";
                    alert(data.message);
                }
            });
```