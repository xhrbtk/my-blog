##端口
```
21端口-FTP
80端口-HTTP
93端口-DNS
443端口-HTTPS
1080端口-SOCKS代理
```
## OSI七层模型指什么？
```
应用层-表示层-会话层-传输层-网络层-数据链路层-物理层
五层协议：应用层-传输层-网络层-数据链路层-物理层
```
## HTTP的工作原理是什么
```
- 用户使用客户端访问URL，客户端与服务端建立连接
- 客户端向服务端发送请求
- 服务器接收到请求处理后返回响应
- 客户端接收响应后断开连接

```
##URI的格式是什么？常见的协议有哪些
![image.png](https://upload-images.jianshu.io/upload_images/8649258-3909da9c58b4176f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
与HTTP关系密切的协议：IP、TCP、DNS
```
## HTTP协议有几种和服务器交互的方法
```
基本方法有4种：get，post，put，delete。一个url地址，它用于描述一个网络上的资源，而http中的get，post，put，delete对应着这个资源的查，改，增，删4个操作。
HEAD:获取报文首部
OPTIONS：查询针对请求URI指定资源支持的方法
TRACE：让服务器端将请求通信环返回给客户端
CONNECT：要求在于代理服务器通信时建立隧道，常与SSL或TLS一起包装使用，也就是HTTPS

```
## 状态码200，301， 304，403,404,500，503分别代表什么意思
```
200:请求成功
301：重定向
304：请求资源没变化，告诉浏览器用本地缓存
403：服务器理解客户端的请求，但是禁止访问
404：找不到指定位置资源
500：服务器遇到了意料不到的情况，不能完善客户端的请求
502：代理坏掉了
503：由于临时的服务器维护或者过载，服务器当前无法处理请求。这个状态是临时的，并且将在一段时间以后恢复。
504：找到网关，但是请求超时，没有返回请求
```
## 报文有哪几部分组成？
![jk](https://upload-images.jianshu.io/upload_images/8649258-897c013f022b3526.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 请求头的格式和作用是什么？给个范例截图说明
![image.png](https://upload-images.jianshu.io/upload_images/8649258-9afa1055d384d7eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 首部的格式和作用是什么？给个范例截图说明
![image.png](https://upload-images.jianshu.io/upload_images/8649258-88c336ea249c6206.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 主体的作用是什么？给个范例
![image.png](https://upload-images.jianshu.io/upload_images/8649258-1fd83aa65b2b8c9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 简述浏览器缓存是如何控制的
```
[Expires]:

描述的是一个绝对时间，根据的是客户端时间。用GMT格式字符串表示，如Expires:Thu, 31 Dec 2037 23:55:55 GMT 下次浏览器再次请求同一资源时。先从哭护短缓存中寻找，找到这个资源后，拿出它的[Expires]跟当前的请求时间比较。如果请求时间在[Expires]指定的失效时间之前，就能命中缓存，这样就不用再次到服务器上去缓存一遍，节省了资源。但是正因为是绝对时间，如果客户端时间被随意更改下，这个机制就失效了。所以我们需要[Cache-Control]。
[Cache-Control]

描述的是一个相对时间，在进行缓存命中时，都是利用浏览器时间判断。这两个header可以只启用一个，也可以同时启用，当response header中，[Expires]和[Cache-Control]同时存在时，[Cache-Control]优先级高于[Expires]。
当浏览器对某个资源的请求没有命中强缓存，就会发一个强求到服务器，验证协商缓存是否命中。如果命中，则还是从客户端缓存中加载。协商缓存利用的是[Last-Modified，If-Modified-Since]和[ETag、If-None-Match]这两对Header来管理的。
[Last-Modified]：原理和上面的[expires]相同，区别是它是根据服务器时间返回的header来判断缓存是否存在。但是有时候也会服务器上资源其实有变化，但是最后修改时间却没有变化的情况（这种问题也不容易被定位），这时候我们需要[ETag、If-None-Match]。

[ETag、If-None-Match]：原理与上相同，区别是浏览器跟服务器请求一个资源，服务器在返回这个资源的同时，在respone的header加上ETag的header，这个header是服务器根据当前请求的资源生成的一个唯一标识，这个唯一标识是一个字符串，只要资源有变化这个串就不同。

[ETag、If-None-Match]这么厉害我们为什么还需要[Last-Modified、If-Modified-Since]呢？有一个例子就是分布式系统尽量关闭掉ETag(每台机器生成的ETag都会不一样）

[Last-Modified，If-Modified-Since]和[ETag、If-None-Match]一般都是同时启用。
```
## 下图各个参数是什么意思
![image.png](https://upload-images.jianshu.io/upload_images/8649258-0579d8a8e51c18c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

