> 参考链接：[css实现瀑布流](https://www.w3cplus.com/css/pure-css-create-masonry-layout.html)
* 有如下html结构
```
<style>
  .container{
    column-count: 5;  //用来设置列数
    column-gap: 0;   //用来设置列间距
  }
.container-box1{
    break-inside: avoid;  //设置在表格元素内部避免进行分页的分页行为
}
</style>
<div class="container">
  <div class="container-box1"></div>
  <div class="container-box1"></div>  
 <div class="container-box1"></div>
</div>
```
