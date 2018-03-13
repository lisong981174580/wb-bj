---
title: H5-canvas
tags: 李松,2017.5.23
grammar_cjkRuby: true
---

## 一、canvas 标签

### 概念：
canvas是h5新增的标签，他上面有很多API，可以绘制操作、形状、处理图片、实时视频；
### canvas标签上的属性
#### （1）、width   宽度   没有单位
#### （2）、height  高度  没有单位
#### （3）、id，class,style,title,这些也是所有标签都有的
  
#### 注意：默认宽高300*150
 
#### 浏览器支持情况：IE6-8不支持canvas；

#### 调整canvas宽度：
1.通过宽高属性  一般用宽高属性
2.通过样式表的方式修改


## 二、绘制方法及步骤

### 1、获取到绘图环境 getContext("2d")
 ```
        获取canvas标签，dom对象
        var can=document.querySelector("#can");
        获取绘图环境：getContext,2d环境
 		var ctx=can.getContext("2d");

 ```
 ### 2、添加样式
 
 -修改样式  颜色   可以右四种填色方式
 #### （1）、填充样式  fillStyle
 ctx.fillStyle="#000";
 ctx.fillStyle="red";
 ctx.fillStyle="rgb(255,255,255)";
 ctx.fillStyle="rgba(255,255,255,0.5)";

#### （2）、描边样式 strokeStyle
ctx.strokeStyle="#000";

### 3、绘制填充矩形  fillRect(起点坐标 x , 起点坐标 y ，宽，高)
 
注：圆点坐标在（0,0）点 ，右、下 为正
```
    	//修改颜色样式
		ctx.fillStyle="green";
		//画矩形  四个点， fillRect(起点坐标x,y，宽，高)
		ctx.fillRect(0,0,100,100);
```
### 4、绘制边框矩形 strokeRect(起点坐标x,y，宽，高)

注：圆点坐标在（0,0）点 ，右、下 为正
```
        //修改边框颜色样式    
        ctx.strokeStyle="#000";
        //画描边矩形 四个点， strokeRect(起点坐标x,y，宽，高)    为了使边框是1像素 所以给横竖坐标都加 0.5
        ctx.strokeRect(200.5,200.5,100,100);
```
### 5、清除矩形区域  ctx.clearRect(起点坐标x,y，宽，高);

  ctx.clearRect(起点坐标x,y，宽，高);  可以将画好的矩形区域清除掉
  
### 6、解决浏览器不支持的办法
```
<canvas id="can" width="400" height="400" >
       你的浏览器版本太低，请升级
    </canvas>
    
```
  
### 7、绘制路径
#### （1）、fill()  填充当前绘图（路径）
#### （2）、stroke() 绘制已定义的路径  描边路径
#### （3）、beginPath() 起始一条路径，或重置当前路径
#### （4）、moveTo(x,y) 把路径移动到画布中的指定点，不创建线条
#### （5）、closePath()  创建从当前点回到起始点的路径
#### （6）、lineTo(x,y)  添加一个断点，然后在画布中创建从改点到最后指定点的线条
#### （7）、clip() 从原始画布剪切任意形状和尺寸的区域
#### （8）、quadraticCurveTo(cp1x,cp1y,x,y)  创建一次贝塞尔曲线
参数说明：控制点1，结束点
#### （9）、bezierCurveTo(cp1x,cp1y,cp2x,cp2y，x,y)  创建二次贝塞尔曲线
参数说明：控制点1，控制点2，结束点
#### （10）、arc(x,y,radius，starAngle，endAngle，anticlockwise)  绘制圆形或圆弧
参数说明：圆心、半径  角度(起始角度，终止角度)   是否逆向
#### （11）、 arcTo(cp1x,cp1y,x,y,r)  创建两切线之间的弧/曲线
参数说明：控制点1，结束点,半径
  
### 绘制步骤：
#### （1）、开始新的路径的绘制 beginPath()
#### （2）、绘制所需要的路径
#### （3）、闭合路径closePath() 
#### （4）、对路径进行填充  或者  描边
fill()
stroke();

### 8、透明度 globalAlpha
```
    obj.globalAlpha=0-1；

```
### 9、线条修饰

 lineWidth  调整线条的宽度

### 10、线条端点    lineCap

miter 默认，创建尖角
bevel  创建斜角
round 创建圆角

```
    tex4.beginPath();
    tex4.moveTo(30,90);
    tex4.lineTo(200,90);
    tex4.lineWidth=20;
    tex4.lineCap="square" ;  //这步必须写在闭合路径的里面，填充或描边的前面
    tex4.stroke();
    tex4.closePath();
    

```
### 11、两条线相交拐角类型  lineJoin
#### （1）、miter 默认，创建尖角
#### （2）、bevel  创建斜角
#### （3）、round 创建圆角

### 12、斜接长度  miterLimit  值为number类型  必需在有尖角的情况下使用   
### 13、使用虚线  setLineDash([线长，间距])   使用虚线   接收的是数组
#### 初始化虚线位置：lineDashOffset
```
    tex.lineDashOffset=offset;

```
## 渐变：
### 14、线性渐变 createLinearGradient(x1,y1,x2,y2)
参数说明：createLinearGradient(x1,y1,x2,y2);  起点1为：x1,y1   起点2为：x2,y2

### 15、径向渐变  createRadialGradient(x1,y1,r1,x2,y2,r2) 
参数说明： createRadialGradient(x1,y1,r1,x2,y2,r2)  6个参数   圆点1：x1,y1   半径r1    圆点2：x2,y2  半径r2 
### 16、添加渐变颜色
参数说明：addColorStop(position,color)  两个参数  position为位置  必须为0-1之间的数    color为渐变的颜色
### 操作步骤：
步骤：
   1、创建渐变对象  var lg= createLinearGradient(x1,y1,x2,y2);
   2、添加渐变颜色  lg.addColorStop(position,color);
   3、使用渐变      tex.fillStyle=lg;
### 17、图案样式
#### （1）、创建图片
```
  var img=new Image();
  img.src="1.jpg";
```
####  （2）、createPattern(imge,type)   引用图片
参数说明：imge 是一个图片对象的引用     type是重复方式  repeat  no-repeat   repeat-x   repeat-y 

####  （3）、阴影
 css中 box-shadow:offx offy blur size color inset;
 
 js中： 
  shadowOffsetX    偏移量
  shadowOffsetY
  shadowBlur;  模糊程度
  shadowColor;  颜色
  
####  （4）、截图工具

#### 获取截图 getImageData(画布坐标x,y,宽，高)；  
#### 放置截图 putImageData(图片数据对象，放在画布x,y,截图x,y,截图宽，高)；


### 18、文本样式  filltext

```

    // 绘制文本：
    ctx.filltext('张三',0,10);   //内容 坐标x  坐标y
    
    // 修改文字字体（默认10px）
    ctx.font:"16px arial";      //修改文字样式（字体大小，字体）
    
    // 修改文字位置   水平对齐方式    start(默认)
    text.textaAlign='left/right/center/end/start(默认)'; //水平对齐方式
    
    // 修改文字位置   垂直对齐方式   alphabetic(默认)
    textBaseline='top/hanging/middle/alphabetic(默认)/ideographic/bottom'; //垂直对齐方式
    
    // 测量文本大小
    measureText('');

```

  