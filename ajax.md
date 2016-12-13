# 简谈AJAX
---
```
    最近学习过程中遇到了难题，就是前后台是如何交互的？，我认为这在工作中是很重要的一部分。
    抱着一颗好奇的心去搜索相关资料，整理了两天，大致了解ajax的流程，
    所以就想记录一下自己的见解，肯定会有不对的地方，但是人总是要犯错，知道自己错在哪里才能更好地前进。
```
##  ajax就是 Asyncronous javascript and xml  异步的javascript和xml。
---
- ajax 不是一门新的技术，而是对现有技术的综合利用。
- ajax 是一门可以不重载整个网页的情况下，实现对该网页某部分进行刷新的技术。

- ajax最核心的部分是XMLHttpRequest对象，这个对象是javascript里的对象，可以通过这个对象与后台服务器进行交换数据。

   在我看来： ajax请求可以分为三大部分：

一. 创建XHR对象。
```js
        var XHR=new XMLHttpRequest();

```
二. 向服务器请求数据。
```js
        XHR.open("method","url","bool值");
        第一个参数 //  method是你向服务器请求数据的方式 get/post
        第二个参数 // url是你要访问服务器上文件的位置
        第三个参数 // bool值 true或者false  true代表是异步  false代表同步。

        XHR.send();
```

三. 监听服务器返回的数据。
```js
    XHR.onreadystatechange=function(){
        if(XHR.readyState==4&&XHR.status==200){
            ..........
        }
    }

   // readyState 返回XMLHTTP请求的当前状态 : 0-4.
//   0 （未初始化）
// 对象已建立，但是尚未初始化（尚未调用open方法）
// 1 （初始化）
// 已调用send()方法，正在发送请求
// 2 （发送数据）
// send方法调用完成，但是当前的状态及http头未知
// 3 （数据传送中）
// 已接收部分数据，因为响应及http头不全，这时通过responseBody和responseText获取部分数据会出现错误，
// 4 （完成）
// 数据接收完毕，此时可以通过通过responseBody和responseText获取完整的回应数据

    // status 状态码  200 表示 服务器成功的收到客户端的请求。

```

