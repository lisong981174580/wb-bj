---
title: JavaScript—尺寸位置篇
tags: 李松,2017.4.30
grammar_cjkRuby: true
---

## 一、获取元素宽高

#### （1）、获取元素（box)的宽
console.log(box.offsetWidth);// 获取元素宽
#### （2）、获取元素（box)的高
console.log(box.offsetHeight);// 获取元素高

## 二、获取页面宽高

### 1、没有兼容性的

#### （1）、获取页面宽
console.log(document.documentElement.clientWidth); 

#### （2）、获取页面高
console.log(document.documentElement.clientHeight);

### 2、有兼容性的

#### （1）、获取页面宽
console.log(window.innerWidth);//不能用在ie8以及ie8以下的版本  

#### （2）、获取页面高
console.log(window.innerHeight); //不能用在ie8以及ie8以下的版本   

## 三、获取元素位置
```
var box3=document.getElementsByClassName('box')[0];
var box4=document.getElementsByClassName('zi')[0];

```
### offsetTop,offsetLeft
#### 1、它测量的距离是，边框外到浏览器边框的距离
#### 2、当他的父元素有定位的时候，测量的是边框外，到有定位属性的父元素边框内的距离。

#### 这里（box3）所有父元素都没有定位
console.log(box3.offsetTop);// 获取元素位置
console.log(box3.offsetLeft);// 获取元素位置

#### 这里（box4）父元素有定位
当要测量的元素的父元素以及他父元素的父元素有定位的时候，量到有定位的元素的边框的里面
console.log(box4.offsetTop);// 获取元素位置
console.log(box4.offsetLeft);// 获取元素位置

## 三、鼠标位置

#### (1)、鼠标到浏览器边框的距离  

var cx=e.clientX ; // 鼠标到浏览器边框的距离     注：在移动端是到视口的距离
var cy=e.clientY;

#### （2）、鼠标到事件源的距离

var ox=e.offsetX ; // 鼠标到事件源的距离
var oy=e.offsetY;

#### （3）、鼠标到屏幕的距离
 
var sx=e.screenX ; // 鼠标到屏幕的距离
var sy=e.screenY;

#### （4）、到页面的距离 

x1=e.touches[0].pageX;// page在pc端用不了   到页面的距离     
y1=e.touches[0].pageY;

```
    aa.onmousemove=function(e){
    
    //当触发事件的时候 e就是一个事件对象，上面保存了事件信息
    // 在旧版本里  e是 window.event
    
    
	var cx=e.clientX ; //鼠标到浏览器边框的距离     注：在移动端是到视口的距离
	var cy=e.clientY;

	var ox=e.offsetX ; //鼠标到事件源的距离
	var oy=e.offsetY;


	var sx=e.screenX ; //鼠标到屏幕的距离
	var sy=e.screenY;

	aa.innerHTML=`cx:${cx}-cy:${cy}`;
    aa.innerHTML+=`<br>`;

	aa.innerHTML+=`cx:${ox}-cy:${oy}`;
    aa.innerHTML+=`<br>`;

	aa.innerHTML+=`cx:${sx}-cy:${sy}`;
}

```

## 四、拖拽案例

```


//按下
aa.onmousedown=function(e){

        var flag=true;
		var ox=e.offsetX ; //鼠标到事件源的距离
		var oy=e.offsetY;
//拖动
		this.onmousemove=function(e){
			if(flag){

				var cx=e.clientX ; //鼠标到浏览器边框的距离
				var cy=e.clientY;

				this.style.top=`${cy-oy}px`;
				this.style.left=`${cx-ox}px`;
			}
		
		}

		this.onmouseup=function(){
		// this.onmousemove=null;
			if(flag){
				flag=false;
			}
        }
}

```





















