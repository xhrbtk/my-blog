- url由三部分组成，协议，服务器地址，路径文件。例如：https:www.baidu.com/picture
- http请求方法
```
get:从服务器上获取资源
post：向服务器提交表单
put：向服务器存放文件
delete：删除服务器上的文件
options：用于请求web服务器告知其支持的各种方法
head：和get类似，但并不是先要网页本身，是想要网页的一些信息
```
- 状态码
```
100-199：客户端还在进行一些操作
200-299：用于表示请求成功
300-399 ：文件已经被移动，并且常包含新的地址信息
400-499：客户端错误
500-599：服务器错误
301：重定向：文件永久性的移动了
302：与301类似，但是302不是永久性的移动，只是临时性的
304：本身是为了做缓存，请求资源没变化，告诉浏览器用本地缓存
403：资源不可用，服务器理解客户端的请求，但是禁止访问
404：找不到指定位置的资源
500：服务器遇到了意料不到的情况，不能完成客户的请求
502：代理坏掉了
504：找到网关，但是请求超时，没有返回请求
```
- http报文
```
http报文是简单的格式化数据块，每个报文都包含一条来自客户端的请求或者一条来自服务器的响应，又3个部分组成
1.对报文进行描述的起始行
2.包含属性的首部块
3.可选的包含数据的主体部分
报文分为：请求报文和响应报文
通用首部：客户端和服务器都可以使用的
请求首部：


```










