---
title: LocalStorage和SessionStorage 本地储存和会话储存的用法。
date: 2019-12-02 22:10:59
tags: Javascript
---
首先简单介绍一下LocalStorage和SessionStorage，这两个API都是用在储存数据的，LocalStorage叫做本地储存，SessionStorage叫做会话储存。<!--more-->
LocalStorage本地储存是将数据保存成本地文件，文件永久存在，除非在本地删除，减少了与服务器大量的数据传递。增加用户的体验。
而SessionStorage会话储存并不是一种永久性的储存，顾名思义它的生命周期只在会话中，用户关闭网页即结束会话，储存在SessionStorage储存的数据就会进行销毁。
关于大小，LocalStorage和SessionStorage的储存大小一般都时5MB。
可以在谷歌浏览器中查询到储存的数据：
{% asset_img 01.png This is an image %}
关于LocalStorage和SessionStorage的方法，都有：
setItem(key, value) —— 保存数据，以键值对的方式存储信息
getItem(key) —— 获取数据，将键值传入，即可获取到对应的value值
removeItem(key) —— 删除单个数据，根据键值移除对应的信息
clear() —— 删除所有的数据
key(index) —— 获取某个索引的key

下图主要用LocalStorageAPI做了一个上次登录时间的例子：
{% asset_img 02.png This is an image %}
以上只是本人的一点见解，如有错误请多多包涵！
也可以邮箱联系1031531798@qq.com 本人 进行改正。 谢谢大家！
{% asset_img 04.jpg This is an image %}