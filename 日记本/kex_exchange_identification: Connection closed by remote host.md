## 今天搞完项目准备推到自己的github的时候 突然推不上去了报错内容
```
kex_exchange_identification: Connection closed by remote host
```
## 不清楚原因是什么 通过以下方法解决
```
vim ~/.ssh/config 
// 修改.ssh/config 为并保存退出：
Host github.com
  HostName ssh.github.com
  User git
  Port 443
// 终端执行  ssh -T git@github.com 
```
![image.png](https://upload-images.jianshu.io/upload_images/8649258-265151cfc3806666.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
