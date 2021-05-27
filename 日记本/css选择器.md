## **1.class 和 id 的使用场景?**

*   **id：**

    id属性的值，在当前的page页面要是唯一的。
    根据提供的唯一id号，快速获取标签对象。
*   **class：**

    可以把多个类，放在一个class属性里，但必须用空格隔开；如：class='btnsubmit btnopen'CSS操作，把一些特定样式放到一个class类中，需要此样式的标签，可以在添加此类。

## **2.CSS选择器常见的有几种?**
CSS选择器常见的有5种，分别是：基础选择器、组合选择器、属性选择器、伪类选择器、伪元素选择器。
![image.png](http://upload-images.jianshu.io/upload_images/8649258-3f4bfd0d75d1864a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-13693299c7dc3516.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-9e32cdc34eb56e14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](http://upload-images.jianshu.io/upload_images/8649258-69e1a4fdc174d2bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##3.选择器的优先级是怎样的?对于复杂场景如何计算优先级？

![image.png](http://upload-images.jianshu.io/upload_images/8649258-ffb328c8e36179f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 复杂场景计算优先级：对于复杂场景的优先级计算，从最高权重的选择器数量开始对比，哪个选择器数量多的就取哪个值优先，如果数量相等，则对比下一级权重的选择器数量，直到得到结果为止。
## 4.a:link, a:hover, a:active, a:visited 的顺序是怎样的？ 为什么？
正确顺序：
a：link
a：visited
a:hover
a:active
原因：

1.当选择器优先级别相同时，后定义的会覆盖先定义的
2.以此类推，当鼠标经过未访问链接，同时有link和hover属性，
由于后定义的覆盖先定义的，所以hover在后面
以此类推，当鼠标经过已访问链接，同时有visited和hover属性，
由于后定义的覆盖先定义的，所以hover在link和visited后面
##5以下选择器分别是什么意思?
![image.png](http://upload-images.jianshu.io/upload_images/8649258-57dd0df90e0d05c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 列出你知道的伪类选择器。
:link、:visited、:active、:hover、:focus、:first-child、:first-of-type、:last-of-type、:nth-child(n)、:nth-of-type(n)

- div:first-child和div:first-of-type的作用和区别。
div:first-child：选择属于其父元素的第一个子元素的每个 <div> 元素;
div:first-of-type:选择属于其父元素下所有同类型元素中的第一个 <div> 元素。
两者区别是：前者选择的是父元素下的第一个子元素下所有的 <div>元素，后者选择的是父元素下所有同类型元素之间的第一个<div>元素。

## 运行如下代码，解析下输出样式的原因。
![image.png](http://upload-images.jianshu.io/upload_images/8649258-be634a27ff717b3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](http://upload-images.jianshu.io/upload_images/8649258-c020afcb1d0aa823.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**.item1:first-child{color: red;}**

：表示父元素 <div class="ct">下的第一个子元素 <p>下的所有带类item1的字体颜色都变红，因为第一个子元素里面只有一个类item1，所只有 <p class="item1">aa</p>的字体变红了；

**.item1:first-of-type{background: blue;｝**

：表示父元素 <div class="ct">下的所有同类型元素中的第一个带类item1的背景颜色变蓝，因为 <p>元素只有一个，所以 <p class="item1">aa</p>的背景发生改变，而 <h3>元素有两个，所以只有第一个 <h3 class="item1">bb</h3>背景发生改变。


