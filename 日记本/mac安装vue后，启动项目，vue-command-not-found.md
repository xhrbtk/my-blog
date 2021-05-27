最近配置新的mac，全局安装vue和vue-cli之后准备，开始建一个demo试试，结果在执行命令
```
vue init webpack xxx
// vue command not found
```

在.bash_profile中添加
```
//将路径改为自己的路径 在bash_profile中进行添加
export PATH=${PATH}:/usr/local/node/lib/node_modules/lib/node_modules/vue-cli/bin
```
添加完路径之后，执行
```
source .bash_profile
```
在~/.zshrc文件最后，增加一行：
```
source ~/.bash_profile
```
