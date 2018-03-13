---
title:  JavaScript—对象的封装
tags: 李松,2017.5.2
grammar_cjkRuby: true
---

## 一、javascript 分为3部分
#### 1、ECMAScript
#### 2、BOM
#### 3、DOM
注：我们学的都是es5以前的

### 对象：类的实例化

```
function Person(name){

  this.name=name;
  this.leg=2;
  this.eye=2;
  alert("说话");

}

var f=new Person();//实例化对象

var zs=new Person("zs");
var ls=new Person("ls");

```

## 二、对象的特征

### 1、封装
把细节都封装起来，只留下有限的接口，供外界调用。

#### （1）、构造函数

```
function Dog(name){

	this.name=name;
	this.bizi=1;
	this.run=function(){
		alert("我能跑");
	}
}


var dog1=new Dog("zs");
var dog2=new Dog("ls");

//name为参数，zs,ls都是实参；

```

#### （2）、工厂函数
```

function dog(name){

	var Dog={};//新建一个对象
     Dog.name=name;
     Dog.bizi=1;
     Dog.run=function(){
     	alert("我是狗");
     }

	return Dog;
}

var dog1=dog("zs");
var dog2=dog("ls");
var dog3=dog("we");

//name为参数，zs,ls都是实参；

```

#### （3）、prototype函数对象上的属性，指向对象的原型

```
function Person(name){
     this.name=name;
 }

//以下定义该对象的原型
 Person.prototype.say=function(){
 	console.log("说话");
 	console.log(this.name);//微调
}

var zs=new Person("run1");
var ls=new Person("run2");

zs.say();
ls.say();

console.log(zs.name);
console.log(ls.name);

```

对象的原型在代码段上的内容是永久的，是删不掉的（delete）,浏览器一打开就出现，直到关闭。
但可以借助本身的属性进行微调

### 2、继承
（1）、一个类拥有另一个类的属性和方法
（2）、被继承的类称为父类或基类，继承的类称为子类。
（3）、Object 函数  是所有对象的父类

#### （1）、constructor构建该对象的构造函数(属性）
```
var obj=new Object();
console.log(obj.constructor);

```

#### (2)、hasOwnProperty("name")是否有name属性（方法）

```
function AA(){
	this.name="aa";
}

var aa=new AA();

console.log(aa.hasOwnProperty("name"));


```

#### (3)、isPrototypeOf()  是否是另一对象的原型（方法）

```
var arr=new Array();
console.log(Array.prototype.isPrototypeOf(arr));
// isPrototypeOf  是否是另一对象的原型

```

#### (4)、运算符 instanceof（运算符）

```
console.log( arr  instanceof  Array);
// instanceof判断前面对象是否是后面的实例化出来的

```

### 3、继承的运用
#### 继承1：prototype  继承的是固定的东西

```
function Person(){

	this.name="ls";
	this.say=function(){
	
	   console.log(this.name);
	}
}

function Student(){

}

//将一个对象赋值给另一个函数的原型
Student.prototype=new Person();

var stu1=new Student;

console.log(stu1.name);

```

#### 继承2：对象冒充

obj1.fun.call(obj2,args...)
对象obj1的 fun方法  冒充给obj2   使obj2具有了fun的方法   （这里参数是数值）；

obj1.fun.apply(obj2,args...)
对象obj1的 fun方法  冒充给obj2   使obj2具有了fun的方法   （这里参数是数组）；

```
function Person(){
	this.name="per";
	this.say=function(age){

		console.log(this.name +" "+ age);
	}
}

function Student(){
  this.name="stu";
}

var p =new Person();
var s=new Student();

p.say.call(s,18);//call传的参数是数字

p.say.apply(s,[1,2,34,56]);//传的参数是数组

```

#### 继承的顺序:从当前一直往上找，最底层为Object,可以对Object添加属性 

```
Object.prototype.say=function(){
	console.log("顶层的方法");
}
function  person(){
  this.say=function(){
		console.log("父类的方法");//当前的比原型优先级高
	}
}
person.prototype.say=function(){
	console.log("父类原型的方法");
}
function  student(){

	this.say=function(){
		console.log("当前类的方法");
	}
}
student.prototype=new person();
var stu=new student();
stu.say();

```
### 4、this的含义

#### 1、普通函数中 this---window;
#### 2、构造函数中  this---实例化出来的对象;
#### 3、方法中  this---调用该方法的对象;
#### 4、事件处理程序中 this---事件元
#### 5、apply 和 call  this---传入的对象，如果没传， this--window;

## 三、类class  专门用来创建对象的

### 特点：
#### 1、类class  专门用来创建对象的
#### 2、constructor 构造方法
方法写到constructor外时，默认在原型上
#### 4、不存在变量提升，既：必须先有类，才可以创建对象
#### 5、继承(extends)  父类一定写在子类的前面

```
class point{

    //构造方法：
	constructor(x,y){
		this.x=x;
		this.y=y;
	}
	
	//方法写到constructor外时，默认在原型上
	PointPt(){
		console.log(`{x:${this.x},y${this.y}}`);
	}

}


//继承
class colorPoint  extends point{
// colorPoint 继承  point

		constructor(x,y,color){
				super(x,y);//调用父类的构造方法
				this.color=color;
		}

		show(){
			super.PointPt();//调用父类的方法
		}

}

//point对应输出
// var pt =new point(3,2);
// console.log(pt);
// pt.PointPt();



//colorPoint对应输出
var  cpt=new colorPoint(2,4,"red");
console.log(cpt);
cpt.show();
console.dir(colorPoint);

```





