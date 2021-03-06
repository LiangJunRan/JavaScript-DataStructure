### ECMAScript6和Stack类

之前我们是创建了一个可以当做类来使用的Stack函数。JavaScript都是有构造函数，可以用来模拟类的行为。我们声明了一个私有的item变量，它只能被Stack函数/类访问。然而，这个方法为每个类的实例都创建一个items变量的副本。因此创建多个Stack实例的时候，他就不合适了。

#### 使用ES6语法声明Stack类，节省内存。

``` JavaScript

class Stack{
	constructor() {
		this.items = [];
	}
	//添加
	push(element){
		this.items.push(element)
	}
	//输出栈顶
	peek(){
		return this.items[this.items.length-1]
	}
}

```


我们使用ES6简化语法把Stack函数转换成Stack类。这种方法不能像其他语言直接声明，只能在constructor内声明，在其他方法中我们使用this.nameofVariable就可以引用这个变量。
  
  
  
但是这个中的items是公共的。ES6是基于原型的。虽然基于原型的类比基于函数的类更节省空间，<font color="red">但是去不能声明私有属性或方法<font>。

#### ES6中创建私有属性（一）限定作用域Symbol实现类。

ES6新增了一种叫Symbol的基本类型，它是不可变的，可以用作对象属性。

``` JavaScript

let _items = Symbol();

class StackSymbol{
	constructor(){
		this[_items] = []
	}
	//添加
	push(element){
		this[_items].push(element)
	}
	//输出栈顶
	peek(){
		return this[_items][this[_items].length-1]
	}
}

```

我们声明了Symbol类型的变量_items,在类的constructor函数中初始化它的值。  

但是ES6新增的Object.getOwnPropertySymbols方法能够取到类里面的所有Symbols属性。

``` JavaScript

let stackSymbol = new StackSymbol()
		
stackSymbol.push(1)
stackSymbol.push(2)
stackSymbol.push(3)

console.log(stackSymbol.peek())

let objectSymbols = Object.getOwnPropertySymbols(stackSymbol)

console.log(objectSymbols)
console.log(objectSymbols.length)	//1

stackSymbol[objectSymbols[0]].push(4)	//
console.log(stackSymbol.peek())		//4

```

由以上可以看出，访问stackSymbol[objectSymbols[0]]是可以得到_items的，并且 _items是一个数组，是可以进行任意操作的

#### ES6中创建私有属性（二）使用WeakMap实现类。

WeakMap是可以确保属性是私有的  

WeakMap是可以存储键值对的，其中键是对象，值可以是任意数据类型。而且WeakMap的对象在没有其他引用是可以被当做垃圾回收的。  

``` JavaScript

// 声明一个WeakMap类型的变量items
const items = new WeakMap();

class StackWeakMap{
	//在constructor中,以this(Stack类自己的引用)为键,把代表栈的数组存入items
	constructor() {
			items.set(this,[])
	}
	
	//压栈
	push(element){
		let s = items.get(this)
		s.push(element);
	}
	
	//读取栈顶
	pop(){
		let s = items.get(this)
		let r = s.pop()
		return r
	}
}

```

items在Stack类中是私有属性，但是声明是在Stack外的，谁都可以动他。我们可以使用闭包将其包裹起来

``` JavaScript

let StackWeakMap = (functiuon(){
	const items = new WeakMap();
	
	class StackWeakMap{
		constructor() {
				items.set(this,[])
		}
		
		//压栈
		push(element){
			let s = items.get(this)
			s.push(element);
		}
		
		//读取栈顶
		pop(){
			let s = items.get(this)
			let r = s.pop()
			return r
		}
	}
	
	//向外暴露StackWeakMap
	return StackWeakMap;
})()

```

但是用以上方法也是有弊端的，就是扩展类无法继承私有属性。  
至于使用哪种方法，就看具体的业务需求了。