## html5是什么？有哪些新特性？有哪些新增标签？如何让低版本的ie支持html5标签

- html5是超文本标记语言的第5次重大修改，设计目的是为了在移动设备上支持多媒体。
- 新特性：
1.语义特性
 2.本地存储特性
3.设备兼容特性
4.连接特性
5.网页多媒体特性
6.性能与集成特性
7.css3特性
- 新增标签

![image.png](https://upload-images.jianshu.io/upload_images/8649258-f884e193a2eeac64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/8649258-b8673e2eef4ffcad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 兼容低版本浏览器：在head标签中添加：<!–[if lt IE9]> 
<script src=”http://[html5](http://www.webwuyou.com/tag/html5)shiv.googlecode.com/svn/trunk/[html5](http://www.webwuyou.com/93.html).js”></script>
<![endif]–>



## input有哪些新增类型
![image.png](https://upload-images.jianshu.io/upload_images/8649258-e296026025e7adc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 浏览器本地存储中cookie和sesionStorage、localstorage有什么区别？localstorage如何删除
```
共同点：都是保存在浏览器端
不同点：cookie数据始终在浏览器和服务器之间来回传递；cookie数据还有路径的概念，可以限制cookie只属于某个路径下。存储大小限制也不同，cookie数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据。
sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。sessionStorage和localStorage虽然也有存储大小的限制，但是比cookie大的多。
数据有效期不同：sessionStorage：用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。
而localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
cookie值在设置cookie过期时间之前一直有效，即使窗口或浏览器关闭
```
```
//移除localStorage项
localStorage.removeItem("myCat");
```
##  写出如下css3效果的简单事例：
[链接](http://js.jirengu.com/qukuy/1/edit)
```
1.圆角，圆形
2.div阴影
3.2d转换；放大，缩小，偏移，旋转 
4.3d转换：移动，旋转
5.背景色渐变
6.多度效果
7.动画
```
## 实现如下全屏图加过渡色的效果（具体效果随意）[链接](http://js.jirengu.com/nusec/1/edit)
- 写出如下 loading 动画效果 [链接](http://js.jirengu.com/migaj/1/edit) [链接](http://js.jirengu.com/dugaf/1/edit)
