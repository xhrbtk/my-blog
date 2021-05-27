- webpack 默认只支持js json格式的文件
- loader 可以让wbpack支持解析更多格式的文件 比如.css .vue .jsx .ts .sass
- plugin 是作用于webpack整个打包生命周期的机制 每一个插件都会对准一个生命周期 比如webpack打包前 生成资源前
- bundle是打包文件 包含多个chunks代码块，a.js经过处理之后生成的代码片段是chunk
- 配置文件主要分为5部分 ：entrry mode output module plugins
1.entry
```
entry:string array obj{}
entry: './src/index.js'
entry: ['./src/a.js','./src.b.js']
// 对象的方式是多入口 但是对应的出口也要有多个
  entry: {
        build: './src/index.js',
        a: './src/a.js',
        b: './src/b.js',
    },
output: {
        // [name]占位符
        filename: '[name].js',
}

```
2. mode
```
development:相对来说可读性更好
production: 生产模式可读性不强
```
3. output
```
 output: {
        // 把输出的打包文件放在哪里？ path必须是绝对路径
        path: path.resolve(__dirname, './build'),
        //打包好的文件叫什么
        filename: 'build.js',
        // [name]占位符 对应多入口的时候的多出口文件
        // filename: '[name].js',
    }, 
```
4. module
```
 module: {
        // css
        rules: [
            {
                test: /\.css$/,
                // loader 有执行顺序 自后往前
                // 官方推荐一个loader 只做一件事情 style-loader 是将字符串放在html标签里面 css-loader是将css文件转换为bundle文件
                use: ['style-loader', 'css-loader'],
            },
            {
                test: /\.less$/,
                use: ['style-loader', 'css-loader', 'less-loader'],
            },
        ],
    },
```
5. plugins
```
plugins: [
// 每次打包都会清空输出的文件夹 
        new CleanWebpackPlugin(),
//htmlwebpackplugin会在打包结束后，⾃自动⽣生成⼀一个html⽂文件，并把打包⽣生成的js模块引⼊入到该html 中。
        new htmlWebpackPlugin({
            template: './src/index.html',
            filename: 'index.html',
        }),
    ],
```
















