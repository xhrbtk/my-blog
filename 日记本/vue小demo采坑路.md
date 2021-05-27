1.关于解决移动端点击延迟300ms问题，利用fastclick插件解决
2.在某个文件用的比较多的时候，配置webpack下的resolve中的别名选项，可以很大程度上简化路径
3.在子组件中定义data时，一定要是个函数
4.关于图片加载时，造成页面抖动，采用padding-bottom撑开图片的高度，实现图片的自适应
```
.wrapper
  overflow:hidden
  width:100%
  height:0
  padding-bottom:31.25%
  .img
    width:100%
```
5.有某些组件的样式设置可能不符合我们的需要，我们需要重新设置组件，但是我们没有办法更改哪些组件，因此就需要用到穿透组件设置样式
```
.wrapper>>>.swiper-pagination-bullet-active
  background:red
```
6.如果不希望某写文件被提交到github，就可以在.gitignore中添加对应的文件，这样这个文件在下次推送github的时候就不会被提交
7.利用better-scroll插件解决移动端滚动页面的问题
8.实现首页与城市页面关于城市页面的数据共享，可以利用vuex的方式，也可以使用vuex利用acitions--mutations--------》state。vue组件利用dispatch方法调用actions，actions利用commit调用mutations，mutations更改state里的数据。其中action用于存放异步方法或者复杂的同步方法，如果没有使用到异步方法，只是想要简单的更改state的数据，那么可以使用组件调用commit方法调用mutate去更改state的值。还可以引入mapState去简化代码
9.兄弟组件之间传值，可以利用bus总线的方式，还可以利用其中一个子组件传值给父组件（emit触发），父组件传值给另一个子组件（props触发）。
10.优化网络性能，利用keep-alive的方式去减少http请求。由于使用keep-alive，所以也激活了activated生命周期函数。但是由于开启了keep-alive，在每次切换不同城市的时候，页面会直接利用缓存，并不会切换到新的城市页面，所以需要利用activated函数进行页面城市判断，如果城市不同则重新发送ajax请求。
11.当城市为2个字时设置的宽度可能不适用与城市为4个字的时候，因此修改此处的css样式为min-width而不是使用width
12.由于定义了全局事件，这一点很不好，所以要进行全局事件解绑,否则会造成所有的页面都具有这个性能，而且在首页滚动之后导致切换页面之后所处的位置不是新的页面的头部而是旧页面的位置。
```
 mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  unmounted () {
    window.removeEventListener('scroll', this.handleScroll)
  }
```
13.把li标签写为router-link的时候，li标签变为了a标签，但是我们依然希望其仍旧是li标签
```
<router-link tag="li">   这样li标签还是li标签
```
14.如何实现兄弟组件之间的联动，在Alphabet中定义方法handleLetterClick获得被点击的letter然后触发$emit  change事件，事件携带内容为被点击字母，就这样Alphabet将letter传给了父组件，父组件保存了letter之后，将letter传递给list组件，之后再list组件里面监听letter变化，BScroll有一个接口：this.scroll.scrollToElement(letter)滚动到对应字母处。
15.利用setTimeout进行函数节流，节约函数执行次数。
16.如何实现图标页面滑动
```
pages (){
				const pages=[]
				this.list.forEach((item,index)=>{
					//如果为0 则展示在第一页
					//如果为1 则展示在第2页
					const page=Math.floor(index/8)
					//如果数组中没有重复的页数 那么就创建新的页数的数组为空 之后往里面添加item
					if(!pages[page]){
						pages[page]=[]
				
					}
					pages[page].push(item)
					
					
				})
				
				return pages
			}
		}
```
17.动态路由配置
```
  :to=" '/detail/'+item.id"
```
18.利用vue-awsomeswiper，必须使用三层嵌套结构，最外层wrapper，之后swiper，swiper-slide，img
19.城市页面实现滚动需要用到bscroll插件，搜索结果页面需要滚动也是要用滚动插件

























