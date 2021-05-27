## XSS 是什么？如何防范
```
xss是英文Cross-site Scripting的缩写
1.正常用户A提交正常内容，显示在另一个用户B的网页上，没有问题
2.恶意用户H提交恶意内容，显示在另一个用户B的网页上，对B的网页随意篡改
造成xss有几个要点：
1.恶意用户可以提交内容
2.提交内容可以显示在另一个用户的页面上
3.这些内容未经过滤，直接运行在另一个用户的页面上
防范：不要使用innerHTML使用innerText
[参考](https://zhuanlan.zhihu.com/p/22500730?refer=study-fe)
```



## CSRF是什么？如何防范
```
用户在qq.com登录
用户切换到hacker.com(恶意网站)
hacker.com发送一个qq.com/add friend请求，让当前用户添加hacker为好友
用户在不知不觉中添加hacker为好友
用户没有想法这个请求，但是hacker伪造了用户发请求的假象


其原理是攻击者构造网站后台某个功能接口的请求地址，诱导用户去点击或者用特殊方法让该请求地址自动加载。用户在登录状态下这个请求被服务端接收后会被误以为是用户合法的操作。对于 GET 形式的接口地址可轻易被攻击，对于 POST 形式的接口地址也不是百分百安全，攻击者可诱导用户进入带 Form 表单可用POST方式提交参数的页面。


防范：
 服务端在收到路由请求时，生成一个随机数，在渲染请求页面时把随机数埋入页面（一般埋入 form 表单内，<input type="hidden" name="_csrf_token" value="xxxx">）
服务端设置setCookie，把该随机数作为cookie或者session种入用户浏览器
当用户发送 GET 或者 POST 请求时带上_csrf_token参数（对于 Form 表单直接提交即可，因为会自动把当前表单内所有的 input 提交给后台，包括_csrf_token）
后台在接受到请求后解析请求的cookie获取_csrf_token的值，然后和用户请求提交的_csrf_token做个比较，如果相等表示请求是合法的。
[链接](https://zhuanlan.zhihu.com/p/22521378?refer=study-fe)
```
