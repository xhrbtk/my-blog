[jquery.validate多个相同name属性input只验证第一个的问题](https://blog.csdn.net/weixin_33971977/article/details/88278753)

input具有相同name值，用validate校验，它只校验第一个input，后面的input都不校验。解决这个问题，为每个input设置不同的id，对于相同name值，id不同的input，validate会进行全部校验
