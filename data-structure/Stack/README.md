## JavaScript-Stack

栈(Stack)是一种遵从先进后出(LIFO)原则的有序集合。新添的或者待删除的元素都保存在栈的一同端，被称作栈顶，另一端叫栈底。  
也就是说栈是仅在表头进行插入和删除操作的线性表。  

--------

**<font color=#FF0000>使用环境:</font>** 顺序存放，倒叙取出  
栈本身是一种存储的数据结构  
栈有【初始化】、【压栈】、【出栈】、【遍历】和【清空】等主要方法。  
栈操作的是一个一个节点

--------

![栈的模型](http://i2.51cto.com/images/blog/201801/21/796da6488c298dcd907ee5e204d1215b.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_100,g_se,x_10,y_10,shadow_90,type_ZmFuZ3poZW5naGVpdGk=)

<br>
<br>

### 基本操作

#### 1.创建栈

``` JavaScript
function Stack(){
	//属性值和方法声明
}
```

运用数组来保存栈里的元素  
``` JavaScript
let items = [];
```

#### 2.创建添加方法

这个方法负责往栈里添加新元素，只往栈顶添加。

``` JavaScript
this.push = function(element){
	items.push(element)
}
```

#### 3.创建删除元素的方法

删除元素，删除最后一个添加进去的元素

``` JavaScript
this.pop = function(){
	return items.pop()
}
```

删除全部元素,清空栈内数据。  有多种方法，只要是能清空数组内的数据都可以用。这里是直接将栈内的数组等于空数组。
``` JavaScript
// 
this.popAll = function(){
	items = [];
}
```


#### 4.创建查看元素的方法
如何访问栈内的元素，从最后一位开始访问。
``` JavaScript
this.peek = function(){
	return items[items.length-1]
}
```

查看全部数据
``` JavaScript
this.peekAll = function(){
	items.forEach( function(currentValue){
		console.log(currentValue)
	})
}
```

#### 5.查看栈内数据长度

``` JavaScript
this.size = function(){
	return item.length
}
```

#### 6.使用栈

``` JavaScript
// 初始化
var stack = new Stack()

//添加数据
stack.push(1)
stack.push(2)
stack.push(3)
stack.push(4)
stack.push(5)

//输出长度
console.log(stack.size())

//输出最后一个
console.log(stack.peek())

//输出全部
stack.peekAll()
```







