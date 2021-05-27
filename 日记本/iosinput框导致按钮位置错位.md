[文章原有链接]([https://blog.csdn.net/zhangkeke_/article/details/88739521)


> 前端h5混合开发手机端ios  当有input输入时，手机下方弹出键盘使页面上移，当输入完成，键盘消失后页面不能回弹导致下方有空白，按钮不能点击；

> 解决办法： 给input加blur事件 添加事件方法resetDiv，复制以下代码，ok
```
resetDiv(){//ios 兼容，input失去焦点后界面上移不恢复的问题
        setTimeout(() => {
          let scrollHeight = document.documentElement.scrollTop || document.body.scrollTop || 0;
          window.scrollTo(0, Math.max(scrollHeight - 1, 0));
        }, 100)
      }
```
