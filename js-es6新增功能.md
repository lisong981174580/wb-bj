---
title: js-es6新增功能 
tags: 李松,2017.5.8
grammar_cjkRuby: true
---

谷歌：最早兼容es6的浏览器，现代浏览器都可使用es6;

## 一、扩展运算符 ...arr

#### 案例：
var arr=[1,2,3,"123"];
console.log(...arr);

#### 数组合并：
var arr1=[4,5,6];
var arr2=[7,8,9];

## 二、解构  赋值

#### 案例：
var [x,y,z=2]=[1,2,3];// 声明的同时赋值   后面的值会覆盖前面
console.log(x,y,z);


var x=1;
var y=2;
console.log(x,y);//es6引入了块级作用域和类，强类型。
[x,y]=[y,x];
console.log(x,y);
	
	
var {x:a,y:b}={x:1,y:2};// 对象里 匹配的是变量
console.log(a,b);

## 三、函数

### （1）、默认值
```
	function fun(a=5,b=6){
			
			console.log(a,b);
	}
	
	fun();
```
	
### （2）、name  函数名字
```	
	function aa(){
		
	}
	
	console.log(aa.name);
```
### （3）、length  形参接收个数
```	
	function bb(a,b,c,d){
		
	}
	
	console.log(bb.length);
```	
### （4）、箭头函数
	
#### 1、第一种情况  有参数
```
        var f=a=>a;
		//函数名=传入的参数=>返回值；
		
		console.log(f(3));
```	
#### 2、第二种情况  没有参数
	     
```	    
         var f=()=>10;
	     console.log(f());
```	     
#### 3、第三种情况  多个参数
```	     
	     var f=(a,b,c)=>a+b+c;
	     console.log(1,2,3);
```	     
#### 4、返回值有多个参数
```	     
	     var f=(a,b) => {
	     	var c=a+b;
	     	var d=a-b;
	     	return [c,d];
	     }
	     
	     console.log(f(2,2));
```	   
#### 5、对象类型
例子1：
```
       function f6({x,y}){
	    	return x+y;
	    }
	    
	    console.log(f6({x:2,y:3}));
	    
```	
```
	    var f=({x,y})=>x+y;  //小括号代表优先计算
	    
	    console.log(f({x:2,y:1}));
	    
```	

例子2：
```	    
	    
		function  f1({x,y}){
			return {
				a:x,
				b:y
			}
		}
		
		console.log(f1({x:1,y:2}));
```		
``` 
 
 
     var  f2=({x,y})=>({
     	a:x,
     	b:y
     })
		
	 console.log(f({x:1,y:2}));
```	
#### 注意：
1、箭头函数不能当作构造函数	    
2、没有argument对象



## 四、数组 方法

### （1）、遍历数组 forEach（）

```
var arr=[1,2,3,4,5];
arr.forEach(function(val,index){
    console.log(val,index);
});

```

### (2)、元素取平方 forEach（）
```
arr.forEach((val,index) =>{
   console.log(val*val);
})

```

### (3)、筛选元素  filter（）

值大于2，下标小于3，返回由筛选元素组成的新数组

```
var arr5=[1,2,3,4,5,6,7];
var newarr=arr.filter(function(v,i){
    return v>2&&i<3;
})

console.log(newarr);

```
箭头函数：

```
var newarr=arr5.filter((v,i)=> v>2&&i<3);
console.log(newarr);
```

### (3+)、用于找出第一个符合条件的数组成员 find()
> 数组实例的find方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员。如果没有符合条件的成员，则返回undefined。
```
[1, 4, -5, 10].find((n) => n < 0)  
// -5  
[1, 5, 10, 15].find(function(value, index, arr) {  
return value > 9;  
}) // 10  
```

### (3++)、返回第一个符合条件的数组成员的位置 findIndex（）

> 上面代码中，find方法的回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组。
数组实例的findIndex方法的用法与find方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。

```
[1, 5, 10, 15].findIndex(function(value, index, arr) {  
return value > 9;  
}) // 2  

```

### （3+++）、some（） 只要有就返回真

#### 判断数组中有没有符合条件的东西  只要有就返回真
```
var arr=[1,2,3,4,5];
var aa=arr.some(function(v,i){
return  v<3;
})
```

### (4)、every（） 必须所有都满足条件才为真
```
必须所有都满足条件才为真
var arr=[1,2,3,4,5];
var aa=arr.every(function(v,i){
return  v<1;
})

```
## 五、映射：map（）
map()方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。
```
var arr=[1,2,3,4,5];
var newarr7=arr.map(function(v,i){
   return  v*v;
})

console.log(newarr7);

```

## 六、日期

![enter description here][1]

![enter description here][2]


  [1]: ./images/QQ%E5%9B%BE%E7%89%8720170508162339.png "QQ图片20170508162339.png"
  [2]: ./images/QQ%E5%9B%BE%E7%89%8720170508162346.png "QQ图片20170508162346.png"