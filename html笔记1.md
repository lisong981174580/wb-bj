---
-
title: html笔记 
tags: 李松,2017.3.20
grammar_cjkRuby: true
---
## 一、HTML语言

  1.超文本标记语言 ：HTML语言是一种规范，一种标准，通过标记符号来标记要显示的网页中各个部分，他是一种由浏览器解释执行的语言。
  2.创建html方式：！+tab  html5，html:4s +tab  html4 创建的方式。

## 二、html基础

 1. 创建html文本文档，后缀名改为.html。
 2. 创建html主题：！+tab  html5；html:4s +tab  html4 创建的方式。

## 二、介绍html主题

 1. head：描述性文字，他包含的东西不在页面显示。
 2. body：在页面显示的东西。
 3. 标签：以<开头，以>结尾的，结束标签由/.

## 四、标签的分类
 1.双标签：head、body、html
 2.单标签：meta
 3.注释标签 ctrl+/ 
 4.div标签：是一个无意义的容器标签，可以将页面划分为不同的区域。
 5.a标签：超链接标签  a+tab  双标签  有一个href="",里面填的是文件要填的路径，可以是绝对路径，也可以是相对路径，返回上级一次用../,返回上级两次用../../;有一个去下划线的属性，text-decoration:none。

#### 特殊属性
target="_blank"  在空白页面打开
target="_self"  在当前页面打开

 6.图像标签：img标签：单标签；
  重要属性：src:放图像路径；alt:加载失败，再加载失败后起作用。
 7、没有意义的文本标签。
 
### 标签的分类：

 1. 块标签：独占一行，可以设置宽高；如：div标签；
 2. 行内标签：可以在一行显示，不能设置宽高；如：a标签；
 3. 行内块标签：可以在一行显示，也可以设置宽高；如：img标签；
 
#### 标签之间的转换：
 4. 转成行内标签：disply:inline;
 5. 转成快标签：disply:block;
 6. 转成行内块标签：dislay:inline-block;
 





## 五、css语言 

 1. 概念：层叠样式表，是用于将样式信息和内容分离的一种标记。
 2. 创建方法：后缀.css
 3. css语法：｛｝、每个属性结束都有；（英文）
 4.引入：<link rel="stylesheet" href="css/diyike.css">
 5. 命名规范以英文字母开头，后面可以跟字母数字或下划线。
## 六、浏览器控制台 
 
 
 1.查看css是否已经引入：network.
 2.检查元素：elments

## 七、选择器类型


### 常用选择器
 作用：选中页面中的元素
 1. 类名选择器：class，在html中是一个标签，在css中是一个类名，
 2. 标签名选择器。
 3. 后代选择器：在html中表现为父子关系，css中为：父元素（）子元素。
 4. id选择器：在html中体现为id="";在css中体现为#（id名）。
 5. 通用选择器：选中页面中所有标签 ，在css中体现为一个“*”符号。
 6. 伪类选择器：（：hover{}),鼠标移入效果。


 选择器优先级：id（100）>类名（10）>标签名（1）>通用


###其他重要选择器：

####   伪类选择器：
	:link表示未访问
	：visited 已经被访问
	：hover鼠标移入
	：active点击时


	 ： first-letter  选中文本的第一个字符或字母
	 ：first-line 选中文本的第一行



####  子选择器：


父元素  被选元素：first-child  选中作为子元素的第一个元素
       :last-child    选中作为子元素的最后一个元素
	   
	
	：nth-child(n) 选中作为子元素从上往下数第n个元素	
	：nth-child(2n 或者even)    
	
	选中作为子元素的偶数元素
	：nth-child(2n+1或者odd)    
	
	选中作为子元素的奇数元素
	：nth-last-child(n)  选中作为子元素从下往上数第n个元素 
	
	
	:nth-of-type(n)
	选中作为子元素同类型（要选择的子元素）的第n个  
	
	:first-of-type
	选中作为子元素同类型的第一个
	
	:last-of-type
	
	选中作为子元素同类型的最后一个



####  子包含选择器：


	div>p     选中页面中的所有p元素


####  同级选择器

	div+p     div后面相邻的p元素（相邻）
	div~p  div  后面所有的p元素 


####  两个特殊的选择器 
	
	
	
	div:before   在div之前插入内容
	必须做如下工作：
	
	｛content:""  ;   disply:block;}
	
	
	div:after  在div之前插入内容
	必须做如下工作：
	
	｛content:""  ;   disply:block;}
	
	
	一般用来清除浮动：
	｛content:""  ;   disply:block;
	clear:both;
	
	}
	
	
	获取焦点属性：
	
	:focus{  }  一般用在表单元素里
	
	outline:none;消失边框
	
	




 

## 八、一些属性

 1. 圆角：border-radius:50%;圆；
 2. div水平居中：margin：0 auto;
 3. 文本属性：水平居中text-align：center/LEFT/RIGHT.垂直居中line-height:与height的值相同。
 4. 字体属性：字体大小：font-size：16px；文字颜色：color:单词/十六进制/rgb();字体：font-family：“微软雅黑”字体加粗：font-weight；
 5. float:浮动属性，可以加left/right;

#### 特殊属性：

box-sizing:border-box;用padding时常用；
 

## 九、文件的路径

 1. 绝对路径:从根路径开始查找；
 2. 相对路径：通过参考对象找目标，同级文件直接写文件名，进入文件写“一级文件/子文件”，退出文件写“../".

## 十、margin-top bug问题

 1. 现象：给子元素加margin-top 好像作用到了父元素身上。
 2. 解决方法：给父元素加overflow:hidden.

## 十一、盒子模型

 1. 内容content:
 2. 内填充padding：
 3. 边框border:
 4. 外边距margin:
### padding:
 5. 一个值：四个方向；padding:20px;
 6. 两个之：上下  、左右；padding:20PX 20PX;
 7. 三个值：上 、左右、下；padding:20PX 20PX  20PX ;
 8. 四个值：上、右、下、左；padding:20PX 20PX  20PX 20PX;
 9. 单独设置：padding-top上填充；padding-bottom下；padding-right右；padding-left左；
### 边框：
 10. border：2px solid blue;粗细、样式（实线）、颜色；
 11. 同理可以单独设置，如border-top上边框；border-left；左；border-right；右；border-bottom;下；

### 涉及问题

 1.看到的盒子的真实大小：
 宽度=width+padding-left+padding-right+border-left+border-right;
 高度=heigh+padding-top+padding-bottom+border-top+border-bottom;

 2.给同一个区域重复设置外边距时，会显示较大值：
 
 解决方案：给上面的元素设置下边框；给左面的元素设置外边框；

3. margin:0 auto;

4. margin-top的bug问题；
 
 问题：给子元素加margin-top，好像作用在了父元素上；
 解决方案：给父元素加overflow:hidden

### 常见问题

 1. a标签可以按照文本处理，其颜色不可继承；


## 十二、浮动属性

#### 文档流概念：元素正常排列方式，在正常情况下，文档是从上到下，从左到右排列的。

 1. 如果给一个元素增加了浮动属性，元素则脱离了文档流。


#### 浮动的停止：

 1. 遇到另一个是浮动的元素。
 2. 遇到父元素的边界。
####  浮动的运用

 1. 让若干个块标签依次横排，加左浮动；也可以一个在左，一个在右，则一个左浮动，一个有浮动。
 2. 浮动的时候在本层进行浮动。
### bug问题：
 
 3. 问题产生条件：（1）、父元素不设置高度（height:auto:），（2）、子元素浮动。
 4. 产生的错误：父元素的高度撑不开。
 5. 解决方法：（1）、给父元素加（overflow:hidden；）；（2）、在所有浮动元素的元素后面添加一个子元素，给该元素一个css属性：clear:both;(清除浮动）。
 6. a标签设置好宽高后，可以当作行内块标签；


## 十三、代码格式问题

 1. 带链接的图片一般用a标签包img，将a标签转化成块，既：加浮动，然后直接对齐设置宽高，并且将a标签的高度设置为auto。
 2. a链接包图片的时候，当把a链接转化成块后，会发现图像会比a链接少一个像素，此时给img加（disply：block）；
 3. a链接不能直接包在外面，除非转化成块。


## 十四、背景图片

 1. background-color:pink;背景色；
 2. background-image：url();引入背景图片；
 3. background-repeat:no-repeat;禁止重复；
 4. background-position:(1)、单词 lfte/center/bottom/top;(2)、百分比形式；中间必须用空格隔开；（3）、像素（图片精灵）。
 5. background-size:220px;一般写水平尺寸，也就是图片的宽度。
 
 简写形式：background：red url() no-repeat  center  center;依次为：背景色 路径 禁止重复 位置。
 


#### 注意：

 1. 需要更新的图片用img引入；
 2. 不需要更新的图片用background引入；


### 图片精灵

 1. 一张图上有许多截图，主要是调整图片的位置，左上角（0,0）是基点，水平偏移垂直偏移都是负值。

 

## 十五、定位（position）

#### 先不加、再浮动、次定位。
 

 1. 元素设置定位后脱离文档流。
### 作用
 
 2. 将元素固定在任意位置；

### 绝对定位
 1. 父元素：position：relative；
 2. 子元素：position：absolute；
 3. 可用top、left、right、bottom调节；
### 固定定位
 6.position： fixed；
 7.可用top、left、right、bottom调节；
### 重要的居中方式（定位时）
 1. 垂直居中：top：0；bottom：0；margin-top：auto;margin-bottom：auto;
 2. 水平居中：left：0；right：0；margin-left：auto;margin-right：auto;


###  层级属性
 z-index:20; 后面直接加数字，用于固定定位和绝对定位。



## 十六、凡客网站遇到的问题

 1. a标签转化成块包裹img时会出现大小不一现象，此时可将img加（disply:block)将img转化成块。
 2. a标签包裹其他标签时，a标签没有效果，此时应将a标签转化成块，或者不把a标签放在最外层。
 3. 中间lanmu部分应做成一块，然后将其高度设为auto；所有lanmu图片都可用a标签包裹，但是应给a标签加左浮动，将其转化成快标签，负责无效。
 4. 正确的布局方式为：先按正常文档流排列，然后再考虑浮动，次之考虑定位。
 5. 需要更新的图片引用时用img；不需要更新的图片引用时用background；
 6. 定位的时候居中方法：

####方法：
 1. 垂直居中：top：0；bottom：0；margin-top：auto;margin-bottom：auto;
 2. 水平居中：left：0；right：0；margin-left：auto;margin-right：auto;




##  十七、剩余标签

### （1）、字体效果标签（行内标签） 

 1. 换行标签 ：br（单标签）
 2. 粗体：b或
 3. 强调：strong
 4. 斜体：i
 5. 强调：em
 6. 删除线：s
 7. 下划线：u
 8. 水平线标签：hr(单标签），属性：size 高度；width宽度；cilor颜色；
### （2）、标题标签(块标签）
 9. 一级标题：h1
 10. 二级标题：h2
 11. 三级标签：h3
 12. 四级标签：h4
 13. 五级标签：h5
 14. 六级标签：h6
字体大小越来越小

### （3）、区段标签（快标签）

 15. 段落标签：p    不保留格式，一般不嵌套替他标签，除字体效果外。
 16. 段落标签：pre  保留格式，按文档预先排好的方式进行显示。
 17. 

### （4）、列表标签

 1. 无序列表：ul开头，ul结尾，中间任何内容用li体现。ul中type属性可以改变前面序号的形状，circle(空心圆）、disc(实心圆）、square（方形）。
 2. 有序列表：ol开头,ol结尾，中间任何内容用li体现。ol中type属性可以改变前面序号的形状，1(1、23、圆）、i(小写罗马）、I（大写罗马）、a（a、b、c）、A（A、B、C）。
 3. 自定义列表：dl开头，dl结尾，中间用，dt表示条目、dd表示定义。


### （5）、表单标签（行内快标签）

	 1.表单元素：form (双标签）； 属性：action:提交的地址（a.php)    method:提交方式，有get和po   
	   st;git:不安全、快速 ； post:安全
	 2.文本框：input控件： type类型值：text：文本属性  placeholder：提示属性
	 3.密码框：input控件： type类型值：password：密码框属性  placeholder：提示属性
	 4.提交按钮：input控件： type类型值：submit：提交属性  value：默认属性
	 5.重置按钮：input控件： type类型值：reset： 
	 6.单选按钮：input控件： type类型值：ridio：  name：提交给服务器时的名称（必须有）（最少两个选项），且name值必须相同；
	 7.复选按钮：input控件： type类型值：checkbox：多选属性  ；
	 8.文件按钮：input控件：type类型值：file：上传属性  ；
	 9.文本域： textarea   属性：name:提交给服务器时的名称   id:     cols:宽度；rows:高度；  
	 10.自定义按钮：input控件： type类型值bottom; value:默认属性； 
	 11.下拉框select标签（双标签）：里面包option放选项；
	
	```
	
	下拉框:<select name="" id="" size="3"  multiple="multiple">
	
	          <option value=" bsh"> 博士后</option>
	          <option value="bs"  selected="selected<!-- 默认选项 -->">博士</option>
	          <option value="sx">硕士</option>
	          <option value="xs">学士</option>
	        
	
	  </select> 
	
	          
	   
	
	  
	  ```
#### 以上部分value都应该设置一个默认值


	属性：name:提交给服务器识别的名称；id:id名；size:显示几个下拉菜单；multiple：多选（需用ctrl）；
	
	以上部分：name:统一为给服务器提交时的名称；
	


###  （6）、表格标签：table

#### 案例：

	
	   ```
	          <div  class="waibian"></div>
	
	<table border="1" align="center" cellspacing="0" cellpadding="20">
	
	       <tr>
	         <td>王二</td>
	         <td rowspan="">李白</td>
	         <td>张三</td>
	         <td>李四</td>
	         <td>张武</td>
	         <td>徐贵</td>
	      </tr>
	
	        <tr>
	         <td>王二</td>
	         <td>李白</td>
	         <td>张三</td>
	         <td>李四</td>
	         <td>张武</td>
	         <td>徐贵</td>
	       </tr>
	
	       </table>
	       
	       ```
	
	 

#### 重要属性：
     
#####  给table加：
	   colspan="2" 合并列
	   rowspan="" 合并行
	   border="1"加边框
	   align="center"   位置
	   cellspacing="0" 消除单元之间的距离， cellpadding="0"消除单元格与内容之间的距离，这些属性只能给ta  
	   ble加
		
		

#### 加在tr上：
	   文字的水平垂直居中加在tr上，水平用align:center  left  right;  valign="" middle  top  bottom
	
#### 加在td上  

     contenteditable     内容可编辑






    

###  h5新增属性

### 日期：

	 1.date 年月日: ```<input type="date">```
	 2.month  年月: ```<input type="month">```
	 3.week 年周:```<input type="week">  ``
	 4.time  时间:```<input type="week">  ```
	 5.datetime-local 年月日、时间: ``` <input type="datetime-local"> ```
	 
### 范围：
	 6.number  范围（框格方式）: ``` <input type="number" min="0"  max="10" value="5"  step="2"> ```
	 7.range  进度条: ``` <input type="range"  min="0"  max="20"  value="3"   step="2">```

### 正则验证

	 1.邮箱：``` email：  <input type="email">```
	 2.url网址：```<input type="url">```
	 3.电话号码：```<input type="tel"> ```
	 

#### 注意：如果格式不对，则会自动回复错误提示。








## 十八、H5中的语义化标签

	```
         <header>头部标签</header>
         <nav>导航标签</nav>
         <main>主题标签</main>
         <aside>文章的侧栏，与内容有关</aside>
         <section>定义文档的某个区域</section>
         <article>定义文档的独立内容</article>
         <footer>底部</footer>
         <hgroup>  用来包裹标题标签
                <h2>二级标题</h2>
                <h3>二级标题</h3>
    
         </hgroup>
    
          <figure>包裹图像、图片的独立内容
                  
                  <figcaption>图像的标题</figcaption>
    
          </figure>
    
          <code>
                   写要放到页面中的代码
         
          </code>
          
	```
  
  
## 十九、H5中的新增标签
 
       ```
       进度条

        <progress  min="0"  max="10"  value="4"  ></progress>

        范围程度

        <meter  min="0"  max="10"  value="4"></meter>

        音频标签

        <audio src=""   controls="controls"    loop="loop "    autoplay="autoplay"  ></audio>  
        视频标签
        <video src=""  controls="controls"    loop="loop "    autoplay="autoplay" ></video>  

        controls="controls" 
        控件是否向用户显示   

        loop="loop " 循环  值为-1时 无限次播放 
        autoplay="autoplay"  自动播放  


        <canvas   style="width: 400px;height: 300px;background: red;"></canvas> 画布  

       ```
       
       > 转码器mpeg
       
       ```
       
         <audio src=""   controls="controls"    loop="loop "    autoplay="autoplay"  >
                    
                    <source src='1.mp3'  type='audio/mpeg'>
         
         </audio>
       ```
        
        ```
        <video src=""  controls="controls"    loop="loop "    autoplay="autoplay" >
                  <source src='1.mp3'  type='video/mp4'>
        
        </video> 
        ```
#### 透明度属性
  opacity:0.5;o为透明，1为不透明；




##  二十、八卦的写法

#####：在html中只是一个div以下为css样式


		   ```
		       div{
		
			width: 200px;
			height: 100px;
			margin: 40px  auto;
			background: #fff;
		
			border-bottom: 100px  solid  #000;
		
			border-radius: 50%;
		
			position: relative;
		}
		
		
		       div:before{
		
			    content: "";
			    display: block;
		
		       width: 40px;
		       height: 40px;
		       border-radius: 50%;
		
		       border:  30px solid  #000;
		       background: #fff; 
		       position: absolute;
		
		       left: 0;
		       top: 50%;
		
		}
		
		      div:after{
		
			    content: "";
			    display: block;
		
		       width: 40px;
		       height: 40px;
		       border-radius: 50%;
		
		       border:  30px solid  #fff;
		       background: #000; 
		       position: absolute;
		
		       right: 0;
		       top: 50%;
		}
		
		
		    ```


 
##  二十一、特效属性


####  透明度：opacity: ;

 1.  opacity: 0-1;值为0-1之间的数。
 2.  background: rgba( 155,0,0,0.8);0.8为透明度。
 3.  transparent  一般用来做三角形

####  三角形做法：

```
    .sanjiao{


    position: absolute;
    width: 0;
    height: 0;
    border-top: 0.12rem  solid  #01b5ff;
    border-right: 0.12rem  solid   transparent;
    border-bottom: 0.12rem  solid   transparent;
    border-left:  0.12rem  solid  transparent;
    left: 0;
    right: 0;
    margin-left: auto;
    margin-right: auto;
    bottom: -0.24rem;

}


```

####  阴影： box-shadow：；

 3.   box-shadow:  10px（水平） 10px（垂直）   10px （模糊距离）  rgba(0,0,0,0.3)（颜色）;

#### 过渡属性： transition: width  1s  ease   1s;（加在父元素）

 4.  transition-property: with;动画属性,可以用all表示全部属性；
 5.  transition-duration: 2s; 持续时间；
 6.  transition-timing-function: linear（ease); 过度方式函数；
 7.  transition-delay: 0.5s;延时； 

####  偏移属性（2D\3D) （加在过度方式部分）

 8.  transform:translateX(100px);  水平偏移
 9.  transform:translateY(100px); 垂直偏移
 10. transform:translate(100px , 200px); 水平、垂直、偏移 
 11. transform:translate3d(100px,200px,300px); x、y、z的偏移



####  六方体案例：

代码如下：

```

html样式：

    <!-- 建立3d场景 -->
    <div class="zhuanhuan3d">
    <!-- 规定3d属性 -->

    <div class="neirong">

             <div class="main">1</div>
             <div class="main">2</div>
             <div class="main">3</div>
             <div class="main">4</div>
             <div class="main">5</div>
             <div class="main">6</div>
   </div>

</div>

	
	
```

```

css样式：

	.zhuanhuan3d{
	width: 500px;
	height: 600px;
	border: 1px solid red;
	margin:0 auto;
	定义透视点：
	perspective: 1000px;
	人观察的位置
	perspective-origin: left  top;
	}
	
	.neirong{
	
	width: 200px;
	height: 200px;
	border:1px  solid  blue;
	margin:200px  auto  0 ;
	以3d效果显示，如何在3d空间进行显示
	transform-style: preserve-3d;
	定义基点，设置默认基点
	transform-origin: center  center  100px;
	position: relative;
	transition: all  2s  ease;
	
	}


.main{

	width: 200px;
	height: 200px;
	position: absolute;
	background: red;
	font-size: 80px;
	text-align: center;
	line-height: 200px;

	}

.neirong:hover{

        transform: rotateX(360deg)  rotateY(360deg)   rotateX(360deg)  ;  
}

.neirong div:first-child{

	top:0;
	left: 0;
}


.neirong  div:nth-child(2){


	top:0;
	left: 100%;
	background: pink;
	设置基点：水平、垂直
	transform-origin: left  center;
	transform: rotateY(-90deg);
	}


.neirong  div:nth-child(3){

	top:0;
	left: -100%;
	background: yellow;
	transform-origin: right  center;
	transform: rotateY(90deg);
	}

	.neirong  div:nth-child(4){
	top:-100%;
	left: 0;
	background: green;
	transform-origin: bottom  center;
	transform:rotateX(-90deg);
	}


.neirong  div:nth-child(5){
	top:100%;
	left: 0;
	background: blue;
	transform-origin: top  center;
	transform:rotateX(90deg);
	}


.neirong  div:nth-child(6){
	top:0;
	left: 0;
	background: red;
	transform-origin: center  center;
	transform:translateZ(200px);  
	
	}




```


####  隐藏页面中某个元素 visibility 

##### visibility 属性有两种用法：

 12.取值为 hidden 时隐藏元素，并将其所占空间用空白占位。
 13.取值为 collapse 时隐藏表格的一行或一列。
 14.初始值: visible   此时元素可见。




      


  

     


      

       

       

      


 



      


 



 

 

 

 



 



  

 

 








