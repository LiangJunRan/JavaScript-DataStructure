### 使用链表实现队列

因为队列是一种特殊的线性表，所以在存储上也有链式存储和顺序存储两种。

顺序存储我们已经使用数组实现过
现在我们使用链表实现链式存储

#### 优点
1. 可以存储多种数据
2. 可以存储大量数据

#### 代码

``` JavaScript

function LinkStack(){
	
	//节点结构定义
	var Node = function(element,name){
		this.element = element;
		this.name = name;
		this.next = null;
	}
	
	var length = 0; //队列的长度
	var top;		//队首的位置
	var rear;		//队尾的位置
	
	//存数据
	this.push = function(element,name){
		var node = new Node(element,name)
		var current;
		
		if (!top) {
			top = node;
			rear = node;
			length ++;
			return true
		} else{
			rear.next = node
			rear = node
			length++;
			return true
		}
	}
	
	//删除
	this.pop = function(){
		var current = top;
		
		console.log("删除",top)
		
		if(top){
			top = current.next;
			current.next = null;
			length--;
			return  current
		}else{
			return "null stack"
		}
	}
	
	//获取队首
	this.top = function(){
		return top;
	}
	
	//获取队列长度
	this.size = function(){
		return length;
	}
	
	//清空队列
	this.clear = function(){
		top = null;
		length = 0;
		return true
	}
}
```