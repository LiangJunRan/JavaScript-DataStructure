### 使用链表实现栈

因为栈是一种特殊的线性表，所以在存储上也有链式存储和顺序存储两种。

顺序存储我们已经使用数组实现过
现在我们使用链表实现链式存储

#### 优点
1. 可以存储多种数据
2. 可以存储大量数据

#### 代码

``` JavaScript

function LinkStack(){
	
	//节点结构定义
	var Node = function(element){
		this.element = element;
		this.next = null;
	}
	
	var length = 0; //栈的长度
	var top;		//栈顶的位置
	
	//存数据
	this.push = function(element){
		var node = new Node(element)
		var current;
		
		if (!top) {
			top = node;
			length ++;
			return true
		} else{
			node.next = top;
			top = node;
			length++;
			return true
		}
	}
	
	//删除
	this.pop = function(){
		var current = top;
		if(top){
			top = current.next;
			current.next = null;
			length--;
			return  current
		}else{
			return "null stack"
		}
	}
	
	//获取第一个节点
	this.top = function(){
		return top;
	}
	
	//获取栈长
	this.size = function(){
		return length;
	}
	
	//清空栈
	this.clear = function(){
		top = null;
		length = 0;
		return true
	}
}

```