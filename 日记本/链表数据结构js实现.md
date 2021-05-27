#####最近再看学习js数据结构与算法这本书，根据书上的例子和方法实现了一下。记录如下：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>链表</title>
</head>
<body>
<!-- 链表 -->
<script>
  function LinkedList(){
    // 声明链表类
    let Node = function(element){
      this.element = element
      this.next = null
    }
    let length = 0
    let head = null

    // 添加链表方法
    this.append = function(element){
      // 将要添加的元素转换为链表节点 
      // 之后插入链表中
      let node = new Node(element),
      current
      // 添加入链表有两种情况，一种是链表为空，另一种是链表不为空
      // 首先链表为空的时候
      if(head == null){
        // 将head指向要添加的节点的地址
        head = node
      }else{
        // 循环链表 找到最后一项
          current = head
        while(current.next){
          current = current.next
        }
        current.next = node
      }
      length ++
    }
    // 从链表中移除元素
    this.removeAt = function(position){
      // 检查越界值
      if(position > -1 && position < length){
        let current = head,
        previous,
        index = 0;
        // 移除第一项
        if(position === 0){
          head = current.next
        }else{
          while(index++ <  postion){
            previous = current
            current = current.next
          }
          // 将previous与current的下一项链接起来，跳过current，从而移除她
          previous.next = current.next
        }
        length -- 
        return current.element
      }else{
        return null 
      }
    }
    // 返回长度
    this.resize = function(){
      return length
    }

    // 在任意位置插入元素
    this.insert = function(position, element){
      // 检查越界值
      if(position >=0 && position <= length){
        // 将要插入的元素转换为链表节点
        let node = new Node(element),
        current = head,
        previous,
        index = 0
        // 插入位置为头部
        if(position === 0){
          node.next = current
          head = node
        }else{
          // 插入位置为链表中间
          while(index++ <= position){
            previous = current
            current = current.next
          }
          // 找到位置将前后链接起来
          node.next = current
          previous.next = node
        }
        length ++
        return true
      }else{
        return false
      }
    }
    // toString()方法
    this.toString = function(){
      let current = head,
      string = ''
      while(current){
        string += current.element + (current.next ? 'n' : '')
        current = current.next
      }
      return string
    }
    // indexOf()
    this.indexOf = function(element){
      let current = head
      index = 0
      while(current){
        if(element === current.element){
          return index
        }
        index ++
        current = current.next
      }
      return -1
    }
    // 删除
    this.remove = function(element){
      let index = this.indexOf(element)
      return this.removeAt(index)
    }
    // isEmpty
    this.isEmpty = function(){
      // 链表中如果没有元素  则返回true 否则返回false
      return length === 0
    }
    //获得头节点
    this.getHead = function(){
      return head
    }
  }

  // 双向链表
  function DoublyLinkedList() {
    let Node = function(element){
      this.element = element
      this.next = null 
      this.prev = null
    }
    let length = 0
    let head = null
    let tail = null
    // 在任意位置插入新元素
    this.insert = function(position, element){
      // 检查越界值
      if(position >=0 && position <= length){
        let node = new Node(element),
        current = head,
        previous,
        index = 0
        if(position === 0){
          if(!head){
            head = node
            tail = node
          }else{
            node.next = current
            current.prev = node
            head = node
          }
        }else if(position === length){
          current = tail
          current.next = current
          tail = node
        }else{
          while(index++ < position){
            previous = current
            current = current.next
          }
          node.next = current
          previous.next = node
          current.prev = node
          node.prev = previous
        }
        length ++
        return true
      }else{
        return false
      }
    }
  }

</script>
</body>
</html>
```
