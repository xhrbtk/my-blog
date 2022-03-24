发布npm包的过程中会需要npm的账号 密码 和 邮箱这些信息， 在准备好这些信息之后 ，进行以下操作。
- 在发布之前，如果npm源是淘宝镜像源，则需要先切为npm源
```
npm config get registry  // 查看npm当前镜像源
npm config set registry https://registry.npmjs.org/ // 设置npm镜像源
```
- 或者安装nrm工具，管理镜像源
```
// 安装nrm
npm install nrm -g
// 查看可选的源
nrm ls
  npm ---------- https://registry.npmjs.org/
  yarn --------- https://registry.yarnpkg.com/
  tencent ------ https://mirrors.cloud.tencent.com/npm/
  cnpm --------- https://r.cnpmjs.org/
  taobao ------- https://registry.npmmirror.com/
  npmMirror ---- https://skimdb.npmjs.com/registry/
// 切换到淘宝源
nrm use taobao
```
- 在需要发布项目的终端页面 输入npm adduser 根据提示完成以下操作 
![WechatIMG592.jpeg](https://upload-images.jianshu.io/upload_images/8649258-717ada70b31e2c5e.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 执行npm publish 命令发布，如果没有报错，就可以去自己的npm账号看下是否更新成功了