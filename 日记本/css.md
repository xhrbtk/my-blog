### 1\. 块级元素和行内元素分别有哪些？动手测试并列出4条以上的特性区别

*   **块级元素：**
    div p hr form ul dl ol pre table li dd dt dl td th
*   **行内元素：**
    em strong span img a br button input label select textarea code script

| 类别 | 包含 | 宽度 | 高度 | padding |
| --- | --- | --- | --- | --- |
| 块级元素 | 块级元素和行内元素 | 独占一行 | 可以设置高度 | 可以正常设置 |
| 行内元素 | 文本和行内元素 | 根据自身宽度 | 不可设置高度 | 设置上下margin无效 |

### 2\. 什么是 CSS 继承? 哪些属性能继承，哪些不能？

*   **CSS继承**即子类元素继承父元素的属性值
*   **可继承的属性：**
    font-size
    font-family
    color
*   **不可继承的属性：**
    margin
    padding
    border

### 3\. 如何让块级元素水平居中？如何让行内元素水平居中?

（1）**块级元素居中**
自身元素{margin:0 auto;}
（2）**行内元素居中**
父元素{text-align:center;}

### 4\. 用 CSS 实现一个三角形

```
/*css部分*/
.t0{
    width: 0px;
    border-top: 20px solid blue;
    border-right: 20px solid yellow;
    border-bottom: 20px solid green;
    border-left: 20px solid red;
}
/*div部分*/
<div class="t0"></div><br/>

```

[图片上传失败...(image-a657aa-1532011934014)]

隐藏某一条边的方法：
(1)rgba(0,0,0,0);
(2)transparent;

### 5\. 单行文本溢出加`...`如何实现?

```
{
  white-spacing:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}

```

### 6\. px, em, rem 有什么区别

| px | 固定长度单位 |
| --- | --- |
| em | 相对长度单位，相对于父元素 |
| rem | 相对长度单位，相对于根元素（html） |

### 7\. 解释下面代码的作用?为什么要加引号? 字体里`\5b8b\4f53`代表什么?

```
body{
  font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
}

```

1.  设置字体大小为12px，1.5倍行高，tahoma字体，如果没有tahoma字体就使用arial以此类推。
2.  加引号是因为字体名称中间有空格
3.  字体里`\5b8b\4f53`代表宋体，是宋体的Unicode编码

> 查找字体的Unicode编码的方法：
> 
> 1.  打开控制台
> 2.  escape("宋体")，回车
> 3.  将所返回的字符中的'%u'换成'\“即可
