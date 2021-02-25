---
title: File API
date: 2019-11-05 22:14:54
tags: javascript
---
File API 能提供有关文件的信息并允许网页中的 JavaScript 访问其内容。<!--move-->
File API对于某些专门的网站的不可或缺的。现在常用它实现对文件的预览等功能。

File API规定怎么从硬盘上提取文件，直接交给在网页中运行中的Javascript代码。然后代码可以打开文件探究数据，无论是本地文件还是其他文件。注意，关键在于文件会被直接交给JavaScript代码，它并不能修改文件，也不能创建新文件，想要保存任何数据，需要将数据发送到服务器或者保存在本地存储空间中。
在通过File API操作文件之前，首先必须取得文件。使用File API可以直接读取文本文件的内容。 
<!--more-->
例如：
![Loading failed](11.9.png)
readAsText()方法只能处理文本内容的文件，如CSV格式，XML格式，.docx格式和.xlsx格式的文件。 
readAsText()方法只是众多读取文件的方法之一，还有readAsBinaryStrng(),readAsDataURL()和readAsArrayBuffer().

readAsBinaryStrng()方法可以让应用处理二进制编码的数据，但基本上就是把数据保存在一个文本字符串中，效率不高。
readAsArrayBuffer()是对于做数据处理较好的选择，这个方法将数据读到一个数组中，每个数组项代表一字节数据。这套方案的优势是可以用来创建大块数据，然后切分成更小的二进制数据块，以便逐块处理。
readAsDataURL()方法则让我们能方便地取到图片数据。


Web应用通过requestFileSystem方法来访问本地文件系统，该方法是全局的：
requestFileSystem(type, size, successCallback, opt_errorCallback);
 
第一个参数表示存储的类型，有两个值可以选择，TEMPORARY或 PERSISTENT。使用TEMPORARY的话，存储的数据会由浏览器自行决定何时清除。PERSISTENT则表示只能由你的程序来决定何时清除数据。
第二个参数是数字，表示你希望使用多大的空间，单位是MB，后两个参数分别是请求成功和失败（可选）的回调方法。
如果一切顺利的话，系统会调用成功的回调函数，并传入一个FileSystem对象，所有File API或多或少都需要基于此对象来使用。

原文链接：https://blog.csdn.net/xiexingxi/article/details/75825496