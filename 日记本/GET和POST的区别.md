- get和post本质上并没有区别
> get和post是HTTP协议中两种请求方法
> HTTP的底层是TCP/IP。所以get和 post的底层也是TCP连接。get和post能做的事情是一样的。如果给get加上request body，给post加上url采纳数，技术上是可以的。
> HTTP只是个行为准则，TCP才是get和post怎么实现的基本。
>不同的浏览器和服务器就是不同的运输公司。为了保证单次运输的质量，会限制每次的运输量，大多数浏览器通常会限制url长度在2k个字节，而大多数服务器最多处理64k大小的url。超过的部分不会处理。如果你用get服务，在requestbody里偷偷藏了数据，不同服务器的处理方式也是不同的，有些服务器会帮你卸货，读出数据，有些服务器直接忽略。所以，虽然get可以带requestbody，也不能保证一定被接收到。
- get和post的一个重大区别
> get产恒一个TCP数据包，post产生两个TCP数据包。对于get方式的请求，浏览器会把http header和data一并发送出去，服务器响应200返回数据。对于post，浏览器先发送hedaer，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）
因为post需要两步，时间上消耗的多一点，看起来get比post更有效。但是get和post都有自己的语义，不能随便混用。据研究，网络环境好的情况下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的tcp在验证数据包的完整性上，有非常大的有点。并不是所有的浏览器都会在post中发送两次包，firefox只发一次。

本文参考：[99%的人都理解错了HTTP中GET与POST的区别](http://www.techweb.com.cn/network/system/2016-10-11/2407736.shtml)
