---
title: JavaScript—事件篇
tags: 新建,2017.4.24
grammar_cjkRuby: true
---


## 一、概念
基于事件驱动的
事件：用户操作或页面的执行
事件源：操作的那个东西
事件处理程序：操作后要干嘛
事件对象：当事件发生时保存一些状态


## 二、鼠标点击事件
### （1）、onclick  单击
### （2）、ondblclick 双击
### （3）、onmousedown  鼠标按下
### （4）、onmouseup    抬起
### （5）、onmouseover  移入
### （6）、onmouseout   移出
### （7）、onmousemove  移动 


## 三、键盘           
### （1）、onkeydown      按下
### （2）、onkeyup        抬起
### （3）、onkeypress     按住

## 四、表单
### （1）、onfocus        聚焦
### （2）、onblur         失去焦点
### （3）、onchange       改变内容
### （4）、onsubmit       提交

## 五、页面
### （1）、onload         页面加载后触发

```
window.onload=function () {

  
 }//页面加载后执行

```

### （2）、监测屏幕的变化

当浏览的尺寸发生变化就会触发它

```
window.onresize=function(){


}

```

#### 案例：漂浮窗

```
window.onresize=function(){ 

 //onresize 检测屏幕的变化
 cw =document.documentElement.clientWidth;
 ch =document.documentElement.clientHeight;
}


```

### （3）、监测鼠标滚轮变化

```
	window.onscroll=function(){
	
	}
	
```	

#### 案例：楼层调转


```
	window.onscroll=function(){
	
	    var sTop=document.body.scrollTop;
	    if(sTop>=400){
	       list.style.display="block";
		}else{
			list.style.display="none";
		}

	
	
	}
	
```	


## 六、事件绑定与事件失效

#### 注：以下在ie8以下不支持  现代浏览器都支持

#### （1）、事件绑定   false冒泡

aa.addEventListener("click",fn1,false); // 事件类型、对象、false是冒泡型事件  trun是捕获型事件
aa.addEventListener("click",fn2,false);

#### （2）、事件失效

aa.removeEventListener("click",fn1,false);

#### 注：以下ie专属

attachEvent("onclick",fn1);// 事件绑定
dettchEvent("onclick",fn2);// 事件失效


## 七、消除事件中的一个兼容性问题

```
  
    aa.onmousemove=function(e){
    
    //当触发事件的时候 e就是一个事件对象，上面保存了事件信息
    // 在旧版本里  e是 window.event
    
    //消除兼容性
     var  ev=window.event || e;
    
    }


```


## 八、键盘事件—重要键


```
    document.onkeydown=function(e){
    
        //e相当于 window.event   以前用它
        
        console.log(e.keyCode);//判断键码
        
        console.log(e.altKey);  //判断是否是alt键
        console.log(e.shiftKey);//判断是否是shift键
        console.log(e.ctrlKey);//判断是否是ctrl键
        
        console.log(e.type);//测试事件类型  是鼠标事件还是键盘事件
        
    }


```
### （1）、判断键码 e.keyCode
```
  console.log(e.keyCode);
```
### （2）、判断是否是alt键 e.altKey
```
  console.log(e.altKey); 
```
### （3）、判断是否是shift键  e.shiftKey
```
  console.log(e.shiftKey);
``` 
### （4）、判断是否是ctrl键
```
  console.log(e.ctrlKey);
```
### （5）、测试事件类型 e.type
```
  console.log(e.type)；
```	
	
	
	
	
	
