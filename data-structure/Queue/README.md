### JavaScript-Queue

队列是遵循FIFO(先进先出)原则的一组有序的项。队列在尾部添加新元素，并从顶部移除元素。最新添加的元素必须在队列的末尾。  

--------

**<font color=#FF0000>使用环境:</font>** 顺序存放，顺序输出  
队列本身是一种存储的数据结构  
队列有【初始化】、【入队】、【出队】、【遍历】和【清空】等主要方法。  
队列操作的是一个一个节点

--------

![队列的模型](https://sfault-image.b0.upaiyun.com/124/395/1243953170-57245f3329084_articlex)


<br>
<br>

### 基本操作

#### 1.创建队列

``` JavaScript

function Queue(){
	//属性值和方法声明
}

```

运用数组来保存队列里的元素
``` JavaScript
let items = [];
```

#### 2.创建添加方法

这个方法负责往队列里添加新元素，只往队尾添加。

``` JavaScript
this.enqueue = function(element){
	items.push(element)
}
```

#### 3.创建删除方法

删除元素，删除第一个添加进去的元素

``` JavaScript
this.dequeue = function(){
	return items.shift()
}
```

清空元素
``` JavaScript
this.deleteAll = function(){
	items = [];
}
```

#### 4.查看元素

查看队头元素
``` JavaScript
this.front = function(){
	return items[0]
}
```

查看全部元素
``` JavaScript
this.print = function(){
	console.log(items.toString())
}
```

#### 查看队列内数据长度

``` JavaScript
this.size = function(){
	return items.length
}
```

#### 6.使用队列

``` JavaScript
// 初始化
var queue = new Queue()

//添加数据
queue.enqueue(1)
queue.enqueue(2)
queue.enqueue(3)
queue.enqueue(4)
queue.enqueue(5)

//输出长度
console.log(queue.size())	//5

console.log(queue)
//输出第一个添加的
console.log(queue.front())	//1

//输出全部
queue.print()				//1,2,3,4,5

```