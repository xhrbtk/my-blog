##css实现图片自适应
```
<style>
  max-width: 100%;
  max-height: 100%;
</style>
<div>
  <img src="./img.png">
</div>
```
##背景图不动 页面内容滚动
[背景图片不动网址参考](http://zhengyitech.com/)
```
<style>
  .seo-counter{
    background: url('./8.jpg') no-repeat center;
    background-size: cover;
    background-attachment: fixed;
    position: relative;
    margin: 20px 0 132px 0;
    border: 1px solid red;
  }
.seo-counter::before{
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background: rgba(255, 195, 35, 0.9);
    z-index: 1;
  }
  .main-content{
    position: relative;
    z-index: 1;
    padding-bottom: 87px;
    border: 1px solid red;
  }
  img{
    width: 100%;
    display: block;
  }
</style>
<div class="seo-counter">
  <div class="main-content">
    <img src="./object3.png">
  </div>
</div>
```
