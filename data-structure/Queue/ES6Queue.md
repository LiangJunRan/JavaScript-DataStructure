### ECMAScript6和Queue类

直接使用Weakmap来实现Queue类  

``` JavaScript

let Queue = (function(){
	
	const items = new WeakMap()
	
	class Queue{
		constructor(){
			items.set(this,[])
		}
		enqueue(element){
			let q = items.get(this);
			q.push(element)
		}
		dequeue(){
			let q = items.get(this);
			let r = q.shift();
			return r
		}
	}
	
	return Queue
	
})();

```