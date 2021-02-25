---
title: 原生JS关于CSS样式的操作
date: 2019-11-01 21:20:12
tags: [javascript,CSS] 
---
<div>
<h3 style="color:red;">方法一：object.style.className</h3>
<span>该方法有两种写法，分别是 obj.style.width="300px"; 和 obj.style="width:300px;" 。这两种都可以达到修改对象样式的效果。这里需要注意在
javascript中“-”是不能被识别的，所以比如你要设置背景图片，用“background-image”会报错，这时候驼峰命名法可以写成“backgroundImage”的形式，就不会报错。
这种方法有很多的局限性。你不能用这种方法来获取内部样式和外部样式，只能用于行内元素，也就是说你如果想或许内联样式或者外部样式，就必须给你的标签设定
一个“style”属性并且给它设定样式。 </span>
</div>
<!-- more -->
<div>
<h3 style="color:red;">方法二：obj.className</h3>
<span>这种方法可以用setAttribute方法来修改对象的class属性从而为其重新绑定一个CSS样式 "obj.setAttribute("class", "style");" 这种方法可以用来更改内联的CSS样式</span>
</div>
<div>
<h3 style="color:red;">方法三：改变外部引入的CSS文件的样式</h3>
<span>同样用setAttribute方法来改变，获取<link>标签对象，改变<link>标签的href来更换外部样式表 
 obj.setAttribute("href","css.css");
</span>
</div>