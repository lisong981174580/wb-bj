---
title: JavaScript—BOM篇
tags: 李松,2017.4.22
grammar_cjkRuby: true
---

## 一、概念

BOM浏览器对象模型，核心对象是window

#### 1、如果是一个全局对象,则他是挂在window上的一个属性

```
var aa=1;//如果是一个全局对象,则他是挂在window上的一个属性
console.log(aa);
console.log(window.aa);
  
```

#### 2、直接用点挂在window上的属性是可以删掉的，而全局变量是不能通过window删的

```
var aa=1;
window.bb=2;
delete window.bb;//可以删掉
delete window.aa;//删不掉
console.log(window.aa);
console.log(window.bb);

```

## 二、window的属性

#### 1、 获取屏幕到浏览器的距离
```
console.log(window.screenLeft);
console.log(window.screenTop); //适用于IE 谷歌   获取屏幕到浏览器的距离

```

```
console.log(window.screenX);
console.log(window.screenY); //适用于火狐 谷歌  获取屏幕到浏览器的距离

```

#### 2、获取浏览器屏幕尺寸 

```
console.log(window.innerWidth);
console.log(window.innerHeight); //不能用在ie8以及ie8以下的版本   

```

```

console.log(document.documentElement.clientWidth); 
console.log(document.documentElement.clientHeight);//通用

```

#### 3、屏幕分辨率

```
console.log(window.screen.width);
console.log(window.screen.height);//屏幕分辨率；


```

## 三、方法

#### 1、鼠标点击后滚动条移动一次

```
scrollTo(); 
```
#### 2、鼠标点击后滚动条移动多次

```
scrollBy();
```
例子：

```

<body  style="height: 3000px">
	
</body>

<script>

//获取body元素
document.getElementsByTagName('body')[0].onclick=function(){

	 // window.scrollTo(0,200);//可以省略window   横向移动  纵向移动      
	    window.scrollBy(0,200);
};

console.dir(window);

</script>

```

## 四、时间函数（方法）

#### （1）、第一种用法

```

function aa( ){
	
	console.log(1);
}

var t=window.setInterval(aa,1000);//每1000毫秒调用一次函数

```
#### （2)、第二种用法

```
var t1=window.setInterval(function(){
	console.log(2);
},1000);//直接在参数上写匿名函数

```

#### （3）、第三种用法

```
//eval();当传入的字符串可以解析为js代码的时候将隐式调用他；
 var t3=setInterval("console.log(3)",500);
 
```

##  五、停止时间函数（方法）

```

function aa( ){
	
	console.log(1);
}

var t=window.setInterval(aa,1000);//每1000毫秒调用一次函数

clearInterval(t);  停止t这个时间函数


```

## 六、延时函数（方法）

```

function aa( ){
	
	console.log(1);
}

var t=setTimeout(aa,3000); //3秒后执行aa

```


## 七、案例

#### 1、输出1-10十个数，每次输出都间隔1000毫秒，到10停止

```
var n=0;
function num(){

	n++;//每调用一次自加一次
	console.log(n);
	if(n==10){

		clearInterval(t);
		
		}
}


var t=setInterval(num,1000);


```

#### 2、鼠标第一次点击浏览器滚动条自动向下移动，第二次点击停止，再点击又继续


```
var flag=true; //定义一个开关

var t;//将t声明为全局变量

document.getElementsByTagName('body')[0].onclick=function(){

    if(flag){


            t=setInterval(function(){
		 		
		 			window.scrollBy(0,200);//间隔200毫秒向下移动一次

		     },1000);


	         flag=false;

    }else{

    	     clearInterval(t);

    	     flag=true;
     }
	


}


```

## 八、子对象

### 1、location  本地

####  属性

##### （1）、获取地址（属性）
```
console.log(location.href);//获取地址

```

#####  （2）、对地址赋值（属性）
```
 location.href="http://www.baidu.com/";// 对地址赋值
```

##### （3）、获取主机名（属性）
```
console.log(location.hostname);  //主机名
```
##### （4）、获取主机名+端口号（属性）
```
console.log(location.host);// 主机名+端口号
```

#### 方法

```
location.reload();  //刷新

location.replace("http://www.baidu.com/");//替换 

location.assign();//跳转


```


### 2、history 历史记录  

#### 属性

```
history.go(1);  前进一页

history.go(-1);  后退一页

history.go(0);   刷新

history.length;  当前的历史记录一共有几条

```

#### 方法

```
history.back();后退

history.forward();前进

```

