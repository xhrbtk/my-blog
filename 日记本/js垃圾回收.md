- 什么是垃圾？
1.如果没有被引用就是垃圾
2.特例：如果三个对象互相引用，没有被外界引用，也是垃圾
- 标记清除算法，从全局作用域开始，标记被引用的对象，直到没有对象可以标记，标记过程结束，然后清除掉未标记的对象
- 引用技术算法，一旦发现某个变量的引用变为0，就回收掉

