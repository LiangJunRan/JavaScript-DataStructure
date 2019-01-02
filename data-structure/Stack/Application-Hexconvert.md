### 使用栈实现进制转换

数制转换  
十进制数N和其他M进制的转换基本原理：N=(N/M)*M+N%M  

#### 需求：
输入一个任意非负十进制整数，打印输出其对应的八进制整数

#### 思路：
因为进制转换过程是从高到低顺序产生进制数的各个数位，而打印输出，一般来说应从高位到低位进行，恰好和计算过程相反。因此我们可以利用栈先进后出特性，将计算过程中得到的顺序进栈，再按出栈序列打印输出纪委与输入相对应的进制数。

#### 代码：

``` javascript

//创建栈 

function Stack(){
	
	//使用数组作为基本数据类型
	var items = new Array();
	
	//添加
	this.push = function(element){
		items.push(element)
	}
	
	//输出单个
	this.peek = function(){
		return items[items.length-1]
	}
	
	//删除
	this.pop = function(){
		return items.pop()
	}
	
	//打印所有
	this.print = function(){
		return items.toString()
	}
	
	//查看栈内数据长度
	this.size = function(){
		return items.length
	}
}

/**
 * num 需要转化的数字
 * base 转化的进制，默认为 10
 * /
function devide(num,base){
	//判断有没有指定的转换类型
	base = Math.floor(base) || 10;
	//判断第一个参数是否为数字
	if(typeof num != "number" || num < 0 || base > 16 || base < 2){
		throw new Error("参数错误");
		return '';
	}
	num = Math.floor(num);
 
	var code = "0123456789ABCDEF";
	// 创建栈 保存数据
	var stack = new Stack();
	var res = '';
	var rem;
	
	// N=(N/M)*M+N%M  
	while(num > 0){
		rem = num % base;
		stack.push(rem);
		num = Math.floor(num/base);
	}
	 
	while(stack.size() > 0){
		res += code[stack.pop()];
	}
	 
	return res;
}
console.log(devide(32,2))
```