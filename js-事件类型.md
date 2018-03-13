---
title: js-事件类型
tags: 李松,2017.5.8
grammar_cjkRuby: true
---

## 一、冒泡型事件流
冒泡型:从确定到不确定的事件触发流程，所有浏览器都支持

box.addEventListener("click",function(e){

｝，false）；

## 二、捕获型事件流

捕获型事件流:从不确定到确定的事件触发流程，ie8及以下是没有的
当是false时是冒泡型，true是捕获型

box.addEventListener("click",function(e){

｝，true）；


## 三、阻断事件流  stopPropagation()

注：ie8以下也有一个
e.stopPropagation();// 阻断事件流   

## 四、事件委派 target  （ie8以下是srcElement）

给子元素添加的事件添加到父元素上，通过冒泡型事件流和e.target完成对事件流的操作

案例：
```
<body>

	<div id="box">
		<div id="big">
			<div class="small"></div>
			<div class="small"></div>
			<div class="small"></div>
			<div class="small"></div>
			<div class="small"></div>
			<div class="small"></div>
		</div>
	</div>

	<button>添加</button>

</body>



var box=$("#box");
var big=$("#big");
var small=$(".small");
var button=$("button")[0];


big.onclick=function(e){

	e.target.style.background="black";//这句话就可作用到small上
}



button.onclick=function(){

	 var small=document.createElement("div");
         small.classList.add("small");
         big.appendChild(small);
}


```