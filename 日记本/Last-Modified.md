在浏览器第一次请求某一个URL时，服务器端的返回状态200，内容是你请求的资源，同时有一个Last-Modified的属性标记（响应头）此文件在服务器端最后被修改的时间，格式类似这样：Last-Modified：Tue，24 Feb 2009
客户端第二次请求此URL时，根据HTTP协议的规定，浏览器会向服务器传送If-Modified-Since报头（请求头），询问该事件之后文件是否有被修改过，如果服务器端的资源没有变化，则自动返回HTTP：304状态码，内容为空，这样就节省了传输数据量。当服务器端代码发生改变或者重启服务器时，则重新发出资源，返回和第一次请求时类似。从而保证不向客户端重复发出资源，也保证当服务器有变化时，客户端能够得到最新的资源。
### Etag工作原理
- http协议规格说明定义Etag为“被请求变量的实体标记”。简单点即服务器响应时给请求URL标记，并在HTTP响应头中将其传送到客户端，类似服务器端返回的格式。
Etag:“5d8c72a5edda8d6a:3239″

客户端的查询更新格式是这样的：

- If-None-Match:“5d8c72a5edda8d6a:3239″
- 如果Etag没改变，则返回状态吗304
- 即：客户端发出请求后，响应头中包含Etag：“5d8c72a5edda8d6a:3239″标识，等于告诉客户端，你拿到的这个资源有标识ID：5d8c72a5edda8d6a:3239。
- 当下次需要发请求索要同一个URI的时候，浏览器同时发出一个if-None-Match请求头，此时报头中信息包含上次访问得到的：ID标识。
- if-None-Match:5d8c72a5edda8d6a:3239“
- 这样，客户端等于缓存了两份，服务器端就会比对二者的Etag。如果if-None-Match为False，不返回200，返回304状态码。
### Expires
- 给出的日期后，被响应认为是过时。需要和Last-Modified结合使用。用于控制请求文件的有效时间，当请求数据在有效期内时客户端浏览器从缓存请求数据而不是服务器端。当缓存中数据失效或过期，才决定从服务器更新数据。

### 如果max-age和Expires同时存在，则被Cache-Control的max-age覆盖。

## [Expires]:
- 描述的是一个绝对时间，根据的是客户端时间。用GMT格式字符串表示，如Expires:Thu, 31 Dec 2037 23:55:55 GMT 下次浏览器再次请求同一资源时。先从哭护短缓存中寻找，找到这个资源后，拿出它的[Expires]跟当前的请求时间比较。如果请求时间在[Expires]指定的失效时间之前，就能命中缓存，这样就不用再次到服务器上去缓存一遍，节省了资源。但是正因为是绝对时间，如果客户端时间被随意更改下，这个机制就失效了。所以我们需要[Cache-Control]。
## [Cache-Control]
- 描述的是一个相对时间，在进行缓存命中时，都是利用浏览器时间判断。这两个header可以只启用一个，也可以同时启用，当response header中，[Expires]和[Cache-Control]同时存在时，[Cache-Control]优先级高于[Expires]。
- 当浏览器对某个资源的请求没有命中强缓存，就会发一个强求到服务器，验证协商缓存是否命中。如果命中，则还是从客户端缓存中加载。协商缓存利用的是[Last-Modified，If-Modified-Since]和[ETag、If-None-Match]这两对Header来管理的。 
1. [Last-Modified]：原理和上面的[expires]相同，区别是它是根据服务器时间返回的header来判断缓存是否存在。但是有时候也会服务器上资源其实有变化，但是最后修改时间却没有变化的情况（这种问题也不容易被定位），这时候我们需要[ETag、If-None-Match]。

2. [ETag、If-None-Match]：原理与上相同，区别是浏览器跟服务器请求一个资源，服务器在返回这个资源的同时，在respone的header加上ETag的header，这个header是服务器根据当前请求的资源生成的一个唯一标识，这个唯一标识是一个字符串，只要资源有变化这个串就不同。

3. [ETag、If-None-Match]这么厉害我们为什么还需要[Last-Modified、If-Modified-Since]呢？有一个例子就是分布式系统尽量关闭掉ETag(每台机器生成的ETag都会不一样）

[Last-Modified，If-Modified-Since]和[ETag、If-None-Match]一般都是同时启用。
