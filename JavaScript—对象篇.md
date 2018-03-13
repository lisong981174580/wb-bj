---
title: JavaScript—对象篇
tags: 李松,2017.4.20
grammar_cjkRuby: true
---


## 一、对象
### 1.名词解释
#### （1）、基于对象
 一切皆对象，以对象的概念来编程
### 2.面向对象编程
#### a.对象
就是人们要研究的任何事物，不仅能表示具体事物，还能表示抽象的规则，计划或事件。
属性的无序集合，每个属性可以存一个值（原始值，对象，函数）
#### b.对象的属性和方法
属性：用数值描述对象的状态
方法：对象具有客实施的动作
#### c.类
具有相同或相似的性质的对象的抽象就是类，对象的抽象，就是类，类的具体化（实例化）就叫做对象。

## 二.对象的创建和声明方式

####  （1）、构造函数

```

function  shouji(){
}
var phone=new shouji();//实例化对象
console.log(typeof phone);
	 
```
#### （2）、json格式

```
var obj={};
console.log(typeof ）；

```

#### （3）、Object方法

```
var obj=new Object();
console.log(typeof obj);

```
 
## 三、添加属性和方法
 
#### （1）.构造函数中属性与方法的添加
 
##### a.声明后添加

```
	     
 function shouji(){

 }

 var phone=new shouji();
 phone.name='小米';
 phone.color='black';
 phone.call=function(){

 	  alert('打电话');
 }

 console.log(phone);
         
```

##### b. 声明的同时添加

```
 function shouji(){

 	this.name='小米';
 	this.color='black';
 	this.call=function(){
 		alert('打电话');
 	}
 }
 var phone=new shouji();
 console.log(phone);
	     
```
	    
	     
#### (2)、json格式中方法和属性的添加

##### a.先声明后添加

```
var obj={};
obj.nam='张三';
obj.age='20';
obj.eat=function(){
   alert('eating');

};

console.log(obj);
	     
``` 
##### b.声明的同时添加

```
 var obj={
 	name:'张三',
 	age:23,
 	eat:function(){
 		alert('吃饭');
 	}
 };

 console.log(obj);

```
#### （3）、Object方法创建的对象中方法与属性的添加

##### a.先声明后添加

```
 var obj1=new Object();
 obj1.name='zhangsan';
 obj1.age='34';
 obj1.play=function(){
 	alert('玩游戏');
 }
 console.log(obj1);
```

##### b. 声明的同时进行添加
```
 var obj1=new Object({

 	name:'李四',
 	sex:'男',
 	eat:function(){

 		alert('吃饭');
 	}
});
 console.log(obj1);


console.log(window);
```	    

## 四、属性和方法的访问

```
function shouji(){

 	this.name='小米';
 	this.color='black';
 	this.call=function(){
 		alert('打电话');
 	}
 }
 var phone=new shouji();
 
```
#### (1)、属性访问

##### a.对象名.属性名

	console.log(phone.name);
	
##### b、对象名['属性名']
	     console.log(phone['name']);
	    
#### (2)、方法的访问

##### a、对象名.方法名（）;
	   
    phone.call();

##### b、对象名['方法名']（）；

	    phone['call']();

## 五、属性与方法的删除
	    
```  

var obj={

    	name:'张三',
    	age:'34',
    	play:function(){
    		alert('打游戏');
    	}
    }
	    
```


#### (1)、删除属性


##### a、delete 对象名[属性名]

	    delete obj['name'];
	    
##### b、delete 对象名.属性名

	    delete obj.name;
	    
#### （2）、 删除方法

##### a、delete 对象名[属性名]

	    delete obj['play'];
	    
##### b、 delete 对象名.属性名

	    delete obj.play;
	    console.log(obj);

## 六、对象的遍历方式


#### （1）、for...in 进行遍历

```		
var aa={

	name:'手机',
	color:'red',
	call:function(){

		console.log('打电话');
	}

}

for(var i in aa){

	console.log(i);//i是属性名，并且是字符串型
	console.log(aa[i]);
}

```


## 七、对象的分类；

### 1. 全局对象  Math
### 2. 本地对象  Array();  string(); Date();

```
    var arr =new Array;
    var arr =[]
    arr.push(1);
```   
### 3. 宿主对象  BOM  DOM;

### 4. 全局对象调用属性或方法

#### (1) 、Math.abs(1);取绝对值

```
alert( Math.abs(1));  
alert( Math.abs(-1)); 

``` 
  
#### (2)、  Math.ceil(1.8);近似值 进1;


- Math.floor(1.8);近似值 去尾;

- Math.round(1.8);近似值 四舍五入;

- Math.random();随机数；

例子:

```
0-9之间的随机数  1-100之间的随机数  -10—10之间的随机数

console.log(Math.floor(Math.random()*10));
console.log(Math.floor(Math.random()*100+1));
console.log(Math.floor(Math.random()*21-10)); // 范围 距离

``` 
#### (3)、最大值、最小值、开方

- Math.min(9,1,4)最小值
- Math.max(8,4,6)最大值
- Math.sqrt(9); // 算数平方根
- Math.pow(9,3);//9的3次方
- Math.pow(27,1/3);//给9开3次根

#### (4)、三角函数

-  Math.sin() // 正弦函数
- Math.cos() // 余弦函数
- Math.tan()

#### (5)、遍历 Math的属性；

- console.dir(Math); 遍历 Math的属性；

#### (6)、圆周率

- console.log(Math.PI); 圆周率；

#### (7)、给数组添加或者删除元素

```
var arr =new Array(1,2,3,5,6,7,8);

console.log(arr.push(4)); 从末尾添加元素，可以追加多个

console.log(arr.push(1,2));从末尾添加多个元素

console.log(arr);

console.log(arr.pop());// 从末尾删除一个元素，只能删一个

console.log(arr.pop(2)); 无效


console.log(arr.unshift(1)); // 从开头添加元素，可以追加多个

console.log(arr.shift(1)); // 从开头删除元素，只能删一个

```
#### (8)、万能给数组添加或者删除元素

传一个参数，表示下标，删除的是下标以及下标之后的元素，返回值是一个被删除元素组成的数组。

```
var arr =new Array(1,2,3,5,6,7,8);
console.log(arr.splice(2,2));// 下标，删除的个数,返回值是[3,5]


console.log(arr.splice(2,0,33,44,55,66,33));// 下标，删除的个数，追加的元素,返回值是一个被追加元素组成的数组，返回值是[ ]

```

#### (9)、新创建一个数组，然后把这两个数组拼接在一块,原先数组不变

```
var arr1=[1,2];
var arr2=[3,2];
console.log(arr1.concat(arr2));// 新创建一个数组，然后把这两个数组拼接在一块,原先数组不变

```
#### (10)、控制台各数据类型颜色

数字蓝色  布尔粉色  字数串黑色


#### (11)、将数组转化为字符串

```
var arr3=[1,2,4,5,6,7,6];
console.log(arr3.join(" ;"));  //给数组元素添加分隔符

```
#### (12)、截取元素（以下标截止）数组、字符串都可以用

```

var arr3=[1,2,4,5,6,7,6];
console.log(arr3.slice(2,5));  //截取元素  第一个元素的下标下标，最后一个元素的下标

console.log(arr3.slice(-5,-1)); //反向截取元素

```
#### (13)、截取元素（以数量截取）
```
var  str=[23,45,67,89,77,54,45,45,3,54,45];
str.substr(2,5) //从下标2开始取5个
```
#### (14)、 给字符串排序

```
var arr4=[1,2,4,5,6,7,6];
console.log(arr4.sort() ) //给字符串排序

```
常用方法：

```
function aa(a,b){

   return a>b;

}

function bb(a,b){

    return a<b;


}


console.log(arr4.sort(aa)); 升序
console.log(arr4.sort(bb)); 降序

```

字符串不是对象，但会隐式创建对象
```
eval();
当传入的字符串可以解析为js代码的时候将隐式调用他；


var str ="abc";
console.dir(str);   //字符串不是对象，但会隐式创建对象

```
#### (15)、获取字符串中对应下标的字符
```
var str ="abc";
console.log(str.charAt(1));1为下标

```
#### (16)、 文字编码和反编码   
```
var str1="李阳";

console.log(str1.charCodeAt());  //编码

console.log(String.fromCharCode(26446));  //反编码

```
#### (17)、找到字符串第一个需要查找的字符并返回下标 
```
var str4="hjfdhuyrfhuyfrg";
console.log(str4.indexOf("h"));  //找到第一个h并返回下标
     
```  
#### (18)、找到字符串最后一个需要查找的字符并返回下标 
```
var str4="hjfdhuyrfhuyfrg";
console.log(str4.lastIndexOf("h")); //找到最后一个h并返回下标

```
#### (19)、替换元素 

```
var str4="hjfdhuyrfhuyfrg";

console.log(str4.replace("d","wwww"));//将d替换为www

```
 
#### (20)、大小写转化
``` 
var  str4="hafhjfbhfdsngbfsjgjs";

     console.log(str4.toUpperCase() );  //转化成大写
     
     console.log(str4.toLowerCase() );//转化成小写
     
     console.log(str4);
```
#### (14)、数组字符串互转
```
var str5="a-ss-dd-f-gg-jj";
    console.log( str5.split("dd",3) ); //转化成数组    分隔符  个数

var str6=[34,"dd","hh","jj"];
    console.log(str6.join(" ;")); //转化成字符串

```


#### （15） 遍历对象的属性

```
/*Object.keys（) 方法会返回一个由一个给定对象的自身可枚举属性组成的数组*/
```

#### 三个属性的区别

 - split  转化成数组
 - splice  删除元素或追加元素
 - slice  截取元素

## 八、案例：

#### 1、"img/1.jpg"转化成"img/1.gif"
```
var  str="img/l.jpg";

console.log(str);
console.log(str.replace("jpg","gif"));
```  

#### 2、将uek下标找出来
```  
var str1= "优逸客官网地址:http://www.sxuek.com,优逸客课程体系：http://www.sxuek.com/uisj/,优逸客学生作品：http://www.sxuek.com/sxzp/"

while(str1.indexOf("sxuek")!=-1){

console.log(str1.indexOf("sxuek"));//当不存在时值为-1
str1=str1.replace("sxuek","wwwww");

}

```  




