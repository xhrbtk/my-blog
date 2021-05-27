### 块级元素和行内元素分别有哪些？动手测试并列出4条以上的特性区别
- 块级元素：div,h1-h6,p,hr,form,ul.dl,ol.pre,table,li,dd,dt,tr,td,th
- 行内元素：em,strong,span,a,br,img,button,input,label,select,textarea,code,script
- 特性区别1 块级元素独占一行
- 特性区别2 块级元素的高度，宽度
- 特性区别3 块级元素可以设置marging  padding  但是行内元素设置上下margin padding是不生效的（上下padding在视觉上看起来是有效的，但只是用于撑开边框和背景色，对于其本身的高度是没有影响的）
- 特性区别3 元素宽度在不设置的情况下，是它本身父容器的00%（和父元素宽度一致，除非设定一个宽度）
- 示例连接：http://js.jirengu.com/fisam/6/edit?html,output
###什么是 CSS 继承? 哪些属性能继承，哪些不能？
- 举例说css继承，为body设置font-family样式，那么
- 可继承样式：font-size,font-family,font-weight,line-height,color,text-indent
- 不可继承的样式：border,padding,margin,width,height
###如何让块级元素水平居中？如何让行内元素水平居中?
![image.png](http://upload-images.jianshu.io/upload_images/8649258-c51ac4216e5272e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###用 CSS 实现一个三角形
其实核心就几句话，宽高设置为0，由边框来控制大小，然后边框颜色改为透明，然后更改一遍的边框颜色为自己想要的颜色，就能实现三角形效果
https://xhrbtk.github.io/demos/test/task-8/tri.html
###单行文本溢出加 ...如何实现?
- 为单行文本设置样式：white-space：nowrap；规定段落中的文本不换行overflow：hidden；修剪内容，并且其余内容不可见text-overflow:ellipsis显示省略符号来代表被修剪的文本；
###px, em, rem 有什么区别
- 1、px (pixel，像素)：是一个虚拟长度单位，是计算机系统的数字化图像长度单位，如果px要换算成物理长度，需要指定精度DPI(Dots Per Inch，每英寸像素数)，在扫描打印时一般都有DPI可选。Windows系统默认是96dpi，Apple系统默认是72dpi。
- 2、em(相对长度单位，相对于当前对象内文本的字体尺寸)：是一个相对长度单位，最初是指字母M的宽度，故名em。现指的是字符宽度的倍数，用法类似百分比，如：0.8em, 1.2em,2em等。通常1em=16px。
- 3、rem（root em，根em）：在于使用rem为元素设定字体大小时，仍然是相对大小，但相对的只是HTML根元素。通过它既可以做到只修改根元素就成比例地调整所有字体大小，又可以避免字体大小逐层复合的连锁反应。
- 4 vw,vh:xaingdui单位，1vw为屏幕宽度的1%，兼容性太差
###解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?
- 代码作用：为body设置字体大小，行高，字体
- 加引号作用：例如：hiragino sans当中又空格，如果不加引号，浏览器可能会把它当成两个字体。
- 字体里\5b8b\4f53代表的是宋体的unicode编码，为了防止在写中文的情况下编码不匹配时产生的乱码
![image.png](http://upload-images.jianshu.io/upload_images/8649258-4a2ac62949ac3245.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-5318a22a925ed266.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##代码实现：
- 1.  实现如下效果: 
https://xhrbtk.github.io/demos/test/task-8/85.html
- 2.  实现如下按钮效果
https://xhrbtk.github.io/demos/test/task-8/86.html
- 3.  实现如下表格:
https://xhrbtk.github.io/demos/test/task-8/88.html
- 4. 实现如下三角形
https://xhrbtk.github.io/demos/test/task-8/tris.html
- 5 .实现如下card
https://xhrbtk.github.io/demos/test/task-8/87.html
