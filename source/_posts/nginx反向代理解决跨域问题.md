---
title: nginx反向代理解决跨域问题
date: 2021-2-27 18:31:11
tags: [nginx] 
---
## nginx代理请求
nginx的反向代理可谓是nginx的拿手好戏，本文介绍下使用反向代理来解决请求跨域的问题。
<!--more-->
 1. **首先打开nginx目录下的conf文件中的nginx.config文件，这个文件是nginx的配置文件**
![nginx.config](https://img-blog.csdnimg.cn/20210227221020291.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3psZWphbg==,size_16,color_FFFFFF,t_70)
 2. **编辑nginx.config里的内容**

> 打开nginx.config文件，然后找到server字段，定义代理服务。

```javascript
server {
        listen       80; //监听的端口号
        server_name  localhost; // 域名
		// 默认匹配打开的html文件
        location / {
            root   /usr/local/wx-manage-web/dist/; //文件夹路径
            index  index.html index.htm; // 打开的文件类型
        }
        // 自定义匹配路径 
        //这里/api/代表如果出现localhost:80/api/xxx就会匹配到这个规则而不是默认规则
        location /api/ {
            rewrite  ^.+api/?(.*)$ /$1 break;  //重写路径 删除自定义的前缀。
            proxy_pass http://localhost:8088/;// 重定向的路径
        }
      }
```

> 这样就完成了一个代理服务。当浏览器的地址带有api的时候就会将请求重定向到`localhost:8088/` 从而完成跨域。

 3. **更新nginx**

	
> 修改nginx.config后需要重启nginx，nginx。或者nginx -s stop 停止nginx后再 start nginx 启动nginx 
 

 - 开启nginx
  在控制台进入nginx根目录下输入`start nginx`
 - 关闭
在控制台进入nginx根目录下输入 `nginx -s stop` 停止nginx
 - 重启
在控制台进入nginx根目录下输入`nginx -s reload`即可重新启动

> ps：仅是自己学习过程中的小结


