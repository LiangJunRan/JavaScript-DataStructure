### JavaScript-Link

链表存储有序的元素集合，但不同于数组，链表中的元素在内存中并不是连续放置的。每个元素由一个存储元素本身的节点和一个指向下一个元素的引用（也就是指针或者链接）组成

--------

**<font color=#FF0000>使用环境:</font>** 顺序存放，顺序输出。方便删除，插入操作。对于计算机空间利用率大。  
要访问链表中的一个元素，需要从起点开始迭代列表直到找到所需的元素。

--------

![链表的模型](https://images2017.cnblogs.com/blog/1120165/201712/1120165-20171207161602113-1451349858.png)


<br>
<br>

### 基本操作

#### 1.创建链表

``` JavaScript

function LinkedList(){
	let Node = function(element){
		this.element = element;
		this.next = null; 
	} 
	
	//代表链表的长度
	let length = 0;
	//链表的头结点
	let head = null;
}

```

#### 2.向链表尾部追加元素

向链表对象的尾部添加一个元素时，可能有两个场景，一个是链表为空，添加第一个数据；另一个是链表不为空，向其追加元素。

``` JavaScript

this.append = function(element){
	let node = new Node(element);
	if(head){
		//链表不为空
		//那么将当前的尾结点指向新的节点，然后将尾结点移到新节点。所以我们就可以保证尾结点的下一节点一直为null。
		tail.next = node
		tail = node
	}else{
		//链表为空
		//如果链表为空，添加第一个元素到头结点，那么head的指向就为空，这个时候头结点和尾结点应该是重合，也就是同一数据。
		head = node;
		tail = head;
	}
	length++;
}

```

#### 3.向特定位置添加

``` JavaScript

this.insert = function(position,element){
	let node = new Node(element);
	
	//检查越界
	if (position>-1 && position<length) {
		
		let current = head
		let previous;
		let index = 0;
		
		//添加到第一项
		if(position === 0){
			node.next = current
			console.log(node)
			head = node;
			console.log(head)
		}else{
			while(index++<position){
				previous = current;
				current = previous.next
				console.log(previous)
				console.log(current)
			}
			node.next = current;
			previous.next = node;
		}
							
		length++;
		return true
	} else{
		return null
	}
}

```


#### 4.从列表中移除数据

``` JavaScript

//从列表中移除一项,输入的参数为数据.如果有要删除的则返回删除后的数据,如果没有则返回false
this.remove = function(element){
	
	let nodeAll = head
	
	console.log(head)

	while(nodeAll){
		
		if(nodeAll.element === element){
			
			var a = head
			a = null
			head = head.next
			a.next.next = null
			return 
		}else{						
			if(nodeAll.next.element === element){	
				console.log(nodeAll)
				var a = nodeAll.next
				nodeAll.next = nodeAll.next.next
				a = null
				return 
			}else{
				nodeAll = nodeAll.next
			}
		}
	}
	return false 
}

```

#### 5.从列表的特定位置移除一项

``` JavaScript

this.removeAt = function(position){
				
	//检查越界
	if (position>-1 && position<length) {
		
		let current = head
		let previous;
		let index = 0;
		
		//移除第一项
		if(position === 0){
			head = current.next;
		}else{
			while(index++<position){
				previous = current;
				current = previous.next
			}
			previous.next = current.next;
		}
		
		length--;
		
		return current.element
		
	} else{
		return null
	}
}

```

#### 6.返回元素在列表中的索引

``` JavaScript

//返回元素在列表中的索引.如果列表中没有该元素就返回-1,.
this.indexOf = function(element){
	let nodeAll = head
	let size = -1
	
	if(!nodeAll){
		return size;
	}else{					
		while(nodeAll){
			size++;
			if(nodeAll.element===element){
				return size
			}
			nodeAll = nodeAll.next
		}
	}
}

```