当将input框用fixed定位在手机端底部的时候，在苹果手机上面会出现键盘遮挡input框的问题，但在安卓上面没有问题。解决方法如下：
```
//解决移动端苹果手机固定底部input框被遮挡问题
//这里加定时器的目的在于防止input框一获取到焦点之后，就执行了这个操作，导致这一操作没有很好的执行
//给input框绑定focus事件
onFocus(){
  setTimeout(() => {
    document.body.scrollTop = document.body.scrollHeight
  },300)
}
```
