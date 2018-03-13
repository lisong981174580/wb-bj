---
title: js-移动端事件篇
tags: 李松,2017.5.8
grammar_cjkRuby: true
---


## 一、事件类型

### （1）、ontouchstart  按下
### （2）、ontouchmove  按下后移动
### （2）、ontouchend    抬起

以上对应pc端：

onmousedown
onmousemove
onmoseup


## 二、事件绑定

#### 注：以下在ie8以下不支持  现代浏览器都支持

#### （1）、事件绑定   false冒泡

aa.addEventListener("touchmove",fn1,false); // 事件类型、对象、false是冒泡型事件  trun是捕获型事件
aa.addEventListener("touchmove",fn2,false);

#### （2）、事件失效

aa.removeEventListener("touchmove",fn1,false);

#### 注：以下ie专属

attachEvent("touchend",fn1);// 事件绑定
dettchEvent("touchend",fn2);// 事件失效


## 三、封装函数


#### （1）、双击事件

```
 function  touch_dblclick(obj,fn){
	var flag=0;
	var t;
	obj.addEventListener("touchstart",function(){
		flag+=1;
		if(flag==2){
			fn();
		}

		    t=setTimeout(function(){
 			flag=0;
		},500)

	},false)
}

```
#### (2)、长按事件

```
function  touch_press(obj,fn){
    
    var t;
	obj.addEventListener("touchstart",function(){

		var t=setTimeout(function(){
			fn();
		},3000)

	},false);

	obj.addEventListener("touchmove ",function(){
          clearInterval(t);
	},false);

	obj.addEventListener("touchend ",function(){
          clearInterval(t);
	},false);



}


```

## 四、案例  拖拽

```
<style>
*{
	margin: 0;
	padding: 0;
}
body{
	height: 3000px;
}
#box{
	width: 100px;
	height: 100px;
	background: red;
	position: fixed;
}
</style>

<body>
	<div id="box"></div>
</body>



//鼠标拖拽
var box=document.getElementById('box');
var x1,x2,y1,y2,dx=0,dy=0;
 
box.addEventListener("touchstart",function(e){
	
	var ev=e.touches[0]; //移动端使用第一根指头触发的事件
	 
	x1=e.touches[0].pageX;//page在pc端用不了   到页面的距离     
	y1=e.touches[0].pageY;
	
	box.addEventListener("touchmove",function(e){
	x2=e.touches[0].pageX;
	y2=e.touches[0].pageY;

	this.style.left=dx+(x2-x1)+"px";
	this.style.top=dy+(y2-y1)+"px";

	e.preventDefault();//去掉浏览器默认事件
    },false);

    box.addEventListener("touchend",function(e){
	
	  dx=this.offsetLeft;
	  dy=this.offsetTop;


    },false);

},false);


```


