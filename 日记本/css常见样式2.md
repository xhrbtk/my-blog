## text-align：center的作用是什么，作用在什么元素上？能让什么元素水平居中
- 作用是让行内元素居中，作用在行内元素上或者设置了inline和inline-block的元素上
##IE盒模型和w3c盒模型有什么区别
w3c标准中padding、border所占的空间不在width、height范围内，大家俗称的ie的盒模型width包括content尺寸+padding+border
##*{box-sizing:border-box}的作用是什么
- ie盒模型的效果
##line-height：2和line-height:200%有什么区别
line-height是用来垂直居中文本的
- 区别：line-height：2是它本身高度的两倍，line-height:200%是它父元素文字高度的两倍
##inline-block有什么特性？如何去除缝隙？高度不一样的inline-block元素如何顶端对齐？
- 特性1，既呈现inline特性（不占据一整行，宽度由内容宽度决定）
- 特性2，又呈现block特性（可设置宽高，内外编剧）
- 特性3 缝隙问题
-去除缝隙：1.去掉空白字符2.空白字符的字体设为0--》font-size：0；
![image.png](http://upload-images.jianshu.io/upload_images/8649258-99d0e95a78e11bc9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 高度不一样的inline-block设置顶端对齐：由于在设置display：inline-block之后就具有了行内元素的特性，而行内元素的特性是默认以底部基线对齐，如果要以顶部对齐，需要给元素加一个vertical-align：top。
##css sprite是什么
- 指将不同的图片/图标合并在一张图上
- 使用css sprite可以减少网络请求，提高网页加载性能
##让一个元素“看不见”有几种方式？有什么区别
- opacity：0；透明度为0，整体
- visibility：hidden；和opacity：0类似
- display：none；消失不占用位置
- background-color：rgba（0,0,0,0.2）只是背景色透明
##icon的各种实现方式
- image
- css sprites 精灵图（雪碧图）
- icon  font
- css icon
- svg
##代码
- 1.使用csssripte实现如下效果
csssprites减少了http请求，但是雪碧图无法缩放并且不好修改
https://xhrbtk.github.io/demos/test/task/xuebi.html
- 2.在iconfont上搜索“饥人谷”，使用字体图标实现代码1中的效果
https://xhrbtk.github.io/demos/test/task/icon11.html
###把字体做成图标
1.制作字体文件
2.声明font-family
    1.使用本地链接
     2.使用第三方链接
3.使用font-family
   1.使用html实体
   2.使用css：before
