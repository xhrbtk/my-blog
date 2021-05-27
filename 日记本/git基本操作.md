###重要概念
- 已提交（mommitted）该文件已经被安全地保存在本地数据库中了
- 已修改（modified）修改了某个文件，但还没有提交保存
- 已暂存（staged）把已修改的文件放在下次提交时要保存的清单中
###初次使用要设置姓名和邮箱
```
git config --global user.name "你的姓名"
git config --global user.email xxx@gmail.com
```
###clone项目，用于把一个github上的项目clone（下载）到本地变为本地仓库(点击图中clone of  download按钮，就会显示clone地址，复制在git 中输入即可)
```
git clone git@github.com:xhrbtk/component.git
cd component    //切换到component仓库
```
![image.png](https://upload-images.jianshu.io/upload_images/8649258-12826b3176a04d08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###添加文件
```
#通过命令行创建文件  然后添加内容（可以直接打开component文件夹，然后在文件夹里直接添加文件）
//创建文件
touch a.md
//在文件里写入一个字符串
echo "hello" >a.md
git status
```
###将文件放入暂存区
```
#代表将当前文件夹中所有的新增和删除全部放入暂存区
git add .    
```
###添加文件并提交
```
#把暂存区的更新提交到本地库
git commit -am "add file"
gti status
```
###推送到远程仓库
```
#第一次使用
git push origin master
#在使用过一次之后就可以直接用
git push
```
