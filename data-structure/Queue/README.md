### JavaScript-Queue

队列是遵循FIFO(先进先出)原则的一组有序的项。队列在尾部添加新元素，并从顶部移除元素。最新添加的元素必须在队列的末尾。  

--------

**<font color=#FF0000>使用环境:</font>** 顺序存放，顺序输出  
队列本身是一种存储的数据结构  
队列有【初始化】、【入队】、【出队】、【遍历】和【清空】等主要方法。  
队列操作的是一个一个节点

--------

![队列的模型](data:image/png;base64,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)

<br>
<br>

### 基本操作

#### 1.创建队列

``` JavaScript

function Queue(){
	//属性值和方法声明
}

```

运用数组来保存栈里的元素
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
	return item.length
}
```

#### 6.使用队列

``` JavaScript



```