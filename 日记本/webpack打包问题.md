- 最近在做一个基于node和express的在线便利贴，在测试打包的过程中遇到了 一个问题，提示我需要安装webpack-cli。

在网上搜索之后才知道，在webpack4.0之后，webpack将cli和webpack分成了两个包，在当前目录下使用命令：npm install webpack-cli -D之后，发现自己没有安装webpack，然后就使用命令：npm install webpack -D.之后运行命令：webpack。结果显示并不是很正确，然后又瞅了一眼，发现需要制定打包模式，一个是开发者模式，一个是成产模式。关于这两个模式，大致看了一下，生产模式打包之后对于阅读很不友好，但是体积会小很多，开发者模式对于阅读比较好，所以对于我这种菜鸟级别的测试来说，现在还不是用生产者模式的时候，然后就利用命令行：webpack --mode=production。如果使用开发者模式，就利用命令行：webpack --mode=development
- 配置文件的时候css-loader 要在 less-loader之前。
![image.png](https://upload-images.jianshu.io/upload_images/8649258-86ac0ae979af8257.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- e.js里面不需要的代码一定要删掉  不要注释 不要注释  不要注释
