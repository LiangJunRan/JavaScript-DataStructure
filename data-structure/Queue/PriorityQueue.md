### 优先队列

优先队列就是元素的添加和移除是基于优先级的。比如VIP和普通用户  

实现优先队列的两个方法
1. 设置优先级：为每一个数据设置一个优先等级，然后在添加的时候存放到正确的位置。  
2. 入列操作元素：用入列添加元素，然后按照优先级移除他们。  

设置优先级：
``` JavaScript

function PriorityQueue(){
	
	let items = [];
	
	function QueueElement(element,priority){
		this.element = element;
		this.priority = priority;
	}
	
	this.enqueue = function(element,priority){
		let queueElement = new QueueElement(element,priority)
		
		let added = false;
		
		//循环判断
		for(let i=0;i<items.length;i++){
			
			if(queueElement.priority<items[i].priority){
				items.splice(i,0,queueElement);
				added = true;
				break;
			}
		}
		
		//判断要添加的元素优先级是不是大于任何已知元素
		if(!added){
			items.push(queueElement);
		}
		
	};
	
	this.print = function(){
		for(let i=0;i<items.length;i++){
			console.log(items[i].element,items.priority)
		}
	}
	
}

```