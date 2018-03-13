---
title: html新班级笔记2 
tags: 李松,2017.3.21
grammar_cjkRuby: true
---



## 二十二、浏览器内核


Trident内核：IE浏览器核心内核       -ms-

Wibkit内核：  谷歌浏览器内核         -webkit-        

Presto内核：  opera浏览器内核        -o-

Gecko内核 ： 火狐浏览器内核         -moz-




## 二十三、css3属性



### （1）、圆角：

border-radius: 20px;

一个值：上下左右
两个之：左上和右下  右上和左下
三个值：左上  右上和左下   右下

四个值：左上  右上  右下 左下

 border-top-left:20px; 左上角
 border-top-right:20px; 右上角
 border-bottom-left:20px; 左下角
 border-bottom-right:20px;右下角

### （2）、边框图片：

首先需要有一个边：

border: 1px  solid  red;

border-image-source: url();用来引入边框图片
border-image-width: 定义边框图片的宽度

border-image-slice:20;图片切片  没有单位

图片切片将图片分成九块 

border-image-slice:20  fill;   

加fill可将中间部分显示出来


border-image-repeat: repeat(重复平铺，但有不完整的地方)/round（铺满）/stretch(拉伸)   ;


border-image-outset: 10PX;指定在边框的外部绘制边框图片的位置。


### （3）、背景：


在哪些区域进行显示：

background-clip: border-box;在边框、填充、内容显示；

background-clip: padding-box;填充、内容显示；

background-clip: content-box;内容显示；


从哪个区域开始显示：

background-origin: padding-box;从 padding左上角开始显示，为默认值；
background-origin:border-box;从边框左上角显示
background-origin:content-box;从内容左上角显示


### （4）、   图片尺寸：

background-size: 10px  auto(为默认值，默认为按比例)；

可以填的值：
（1）、像素10px  20px (2)、10px(此时高度自动)

（3）、百分比 10%  20%（宽  高）

（4）、cover
图片显示不完全；宽高中的较小者显示，图片显示不完全

（5）、contain 按图片较大者放置，高度自适应，容器有空白，图片显示完全；

图片显示不完全：

background-size:cover; 按图片较小者放置，高度自适应；

background-size:contain; 按图片较大者放置，高度自适应，容器有空白，；



### （5）、2D转换：

transform: translateX(200px);偏移

transform: rotate(30deg);  旋转

transform: scaleX(2);水平缩放
transform: scaleY(2);
transform: scale(2 ,3); 缩放



transform: skewX(30deg);  x轴斜切
transform: skewY(30deg);  y轴斜切
transform: skew(30deg,30deg);   x轴、y轴同时斜切



###  （6）、 线性渐变（兼容性）：

四种主流浏览器内核+不加内核的：

线性渐变：
background-image: linear-gradient(top ,#ff015d, blue,#ffc000)

起点方向：单词：  left  right top  bottom   上下左右 
	       left  top  左上角
	角度：  90deg;




颜色：十六进制、单词、rgba();


重复线性渐变：

background-image:repeating-linear-gradient(top,red,yellow  10%,blue  20% );

注：百分数为颜色截至的位置。


###  （7）、径向渐变：

 四种主流浏览器内核+不加内核的：


径向渐变：


background-image:-webkit-radial-gradient(circle,red,yellow  10%,blue  20% ,pink 30%);
注：百分数为颜色截至的位置，circle为渐变形状为圆形，默认为椭圆形。


重复径向渐变：


 background-image:-webkit-repeating-radial-gradient(circle,red,yellow  10%,blue  20% ,pink 30%);




### （8）、倒影


 倒影：有浏览器兼容性问题（本身不占空间大小,注意margin）

  -wibkit-box-reflect:above         10px        url()    ;
                        方向     倒影与图像的距离     遮罩
                                                     

方向：


left  right   above上  below下


遮罩：

（1）、没有遮罩。
（2）、图片遮罩 url();
（3）、线性渐变遮罩  -wibkit-linear-gradient(top ,ragb(0,0,0,1), rgba(0,0,0,0.4))

全黑：看得见；
模糊：模糊；



### （9）、 用户界面：

####  段落排版：一般用在p标签。


column-count:3; 分为几列

column-gap:40px;  列与列之间间距

column-rule: 1px  dashed（虚线）  #000; 列与列之间的填充

column-width:200px;每列的最小的宽度


column-fill: balance;是否平衡每列的显示高度（主要用在英文中）


#### 文本域textarea：


resize:none;  不能由用户来调整尺寸

resize:both ；  既能水平方向调节，也可以水平方向调节


resize:horizontal;  水平方向调整


resize:vertical;  垂直方向调整



#### 外轮廓：不占空间：


outline-with:10px;外轮廓宽度、
outline-cilor:red; 颜色
outline-style:solid; 样式
outline-offset:20px; 外凸，偏移数值




#### 文本换行等问题：

width: 200px;
font-size: 50px;

white-space: nowrap;文本不进行换行
overflow: hidden;超出隐藏
text-overflow: ellipsis; 将多余文字变成省略号
text-shadow: 1px  1px 5px #000;给文本添加阴影

-webkit-text-fill-color:red;给文本填充颜色
-webkit-text-stroke-width:2px;描边的宽度；
-webkit-text-stroke-color:yellow;描边的颜色；

word-break：break-all;允许在单词内进行换行（针对中日韩以外的文字）



##   二十三、动画


1、定义动画


```

@keyframes mingcheng(自己起名称){

   from{

	css属性的变化
      }

   to{

     css属性的变化
     
      } 


 或
     0%｛


     ｝


      100%｛


      ｝


}

```



2、绑定到选择器上  animation

    动画名称  
    持续时间 
    延时
    运动曲线
    运动次数：

       1、数字
       2、infinite无数次

    下一周期是否逆向：normal（正常）、alternate(需要逆向)  
    动画完成后保持左后一个状态：forwards;
    动画的暂停或运行：running（运行）  paused（暂停）

  综合写法： animation: mingcheng 2s 1s  ease  2  normal  forwards  running;



## 二十四、图像消失

 1、定义一个元素消失，消失后不占位：display:none;此时应与display：block搭配使用。
 2、也可以定义一个元素是否可见；visibility 属性

##### visibility 属性有两种用法：

 1、取值为 hidden 时隐藏元素，并将其所占空间用空白占位。
 2、取值为 collapse 时隐藏表格的一行或一列。
 3、初始值: visible   此时元素可见。

## 二十五、给父元素加line-height

1、子元素是文本、行内标签、行内块标签，要给父元素加line-height;


## 二十六、 iconfont引入方式

#### （1）、下载代码引入

   1.下载代码，将文件夹名改为iconfont并放置要使用的文件夹中。
   2.再将该文件夹中的iconfont.css文件剪切到css文件夹中；
   3.引入并更改，css中文件路径。
   4.使用时将标签类名起为：inconfont和要使用元素的类名，在css中可查见，切记不用再在该标签中加文字了，因为引入的就是一个文字。
   5.用浏览器直接显示，



#### （2)、在线代码引入

 1.搜索图标建立项目后，点击生成代码，
 2.将代码复制到css中，加上http协议，把加有协议的地方的前后单引号删掉；
 3.要使用那个图标直接复制图标代码，放置在html标签中，记住还应在在该标签的css样式中加上

    font-family: 'iconfont'; 




## 二十七、响应式布局


### （1）、定义
    
   一个网站能够兼容多个终端，而不是为每个终端做特定版本 
```
             @media screen and (max-width: 768px){  }
             @media screen and (min-width: 768px) and (max-width: 992px){}
             @media screen and (min-width: 992px) and (max-width: 1200px){}
             @media screen and (min-width: 1200px){}
```

### （2）、优点
 1、灵活性强，根据不同的显示器，调整设计用户浏览习惯的页面
 2、资源利用率高
 3、有利于用户体验 
### （3）、缺点

 兼容各种设备，工作量大，效率低
 2、代码累赘
 3、辨识度不同 


### （4）、栅格系统

栅格系统：每行平均分成12列，通过预定义类，
          结合媒体查询，形成了强大的响应式。
三种终端：移动端、平板端、pc端
四种类型的屏幕：移动端、平板端、pc小屏、pc大屏
                768>移动端 
                768<平板端<992
                992<pc小屏<1200
                pc大屏>1200
.container宽度固定
.container-fliud 宽度不固定100%

##  二十八、移动端布局

#### 移动端布局：（百分比为主、rem为辅)

app分类：3种

原生、web、中性的


### （1）、 html头部样式


```

	
	
	
	
<head>
	    <meta charset="UTF-8">
	
	    <meta name="viewport" content="width=device-width,initial-scale=1,
	    maximum-scale=1,minimum-scale=1,user-scalable=0">
	    <title>首页</title>
	
	    <link rel="stylesheet" href="css/base.css">
	    <link rel="stylesheet" href="css/index.css">
	    <script  src="js/rem.js"></script>
  </head>
	
	含义： 初时缩放值、允许用户缩放最大值、允许用户缩放最小值、是否允许用户缩放 
	
	flex布局
	
	
	
	
	
	
```


### (2)、原理


  将物理视口变为逻辑视口，一般情况下，物理视口尺寸都为980px

### （3）、布局样式

1、百分比布局
2、rem布局
3、flex布局 

#### 注意：

1、在html中根元素是html标签
2、rem是一个相对于根元素字体大小的单位；


### （4）、a标签包img的bug问题

img标签底部间隙问题：

描述：

a标签或div标签包图片时底部有间隙；不同的fontsize也会影响；


解决方法：

1、给img加disply：blok;
2、给父元素加：font-size:0;
3、给img加 vertical-align:top\bootom;

img{ border:0; }

解决ie6里面难看的边框；




### (5)、两端对齐的bug问题


清除样式：

```
html:
 
 
  <ul class="yangshi1" >
  
	<li><a href=""  class="iconfont icon-pingguo "></a></li>
	<li><a href="">Mac</a></li>
	<li><a href="">iPad</a></li>
	<li><a href="">iPhone</a></li>
	<li><a href="">Watch</a></li>
	<li><a href="">Music</a></li>
	<li><a href="">技术支持</a></li>

	<li><a href="" class="iconfont icon-search" ></a></li>
	<li><a href=""  class="iconfont icon-lock"></a></li>
 </ul>

	
 


css:

  .header-nav  ul{

                width: 100%;

                text-align: justify;

                line-height: 44px;

         }

         .header-nav  ul:after{

                content: "";
                display: inline-block;
                height: 0;
                width: 100%;


         }


         .header-nav  ul li{

                display: inline-block;

         }

```




既：
两端对齐
1、li设置：disply：inline-blok;

2、给ul加：text-align:justify;

3、清除两端对齐大bug：
给ul：after 加： 

content=""disply：inline-blok;
height:0;
width:100%;.


## 二十九、flex布局

### （1）、flex布局：弹性布局

  任何一种容器都可以设为弹性布局：
  如何指定该布局：父元素加：disply:flex;
  注意：设置flex布局以后，子元素的float、clear和vertical-align属性将失效
  flex的基本概念：
    父元素叫容器，子元素叫项目；
    主轴：水平；
    交叉轴：垂直

### （2）、容器的属性：

#### 1、项目的排列方向  flex-direction:

      row(从左到右）/row-reverse(从右到左）、
     column(从上到下）、column-reverse(从下到上）；
  
#### 2、项目的水平对齐方式 （主轴上的）  justify-content;
     flex-start(左对齐）、flex-end(右对齐）
     center(居中对齐）、space-between(两端对齐）、space-around(两端等边距对齐）
     
#### 3、项目的垂直对齐方式（交叉轴） align-items:
         
    flex-start(交叉轴的起点）
    flex-end(交叉轴的终点）、center(中点）、stretch(项目不设置高度时占满整屏幕）

#### 4、项目的包裹方式：主要用来控制项目是否换行；

   flex-wrap:nowrap（默认值，不换行）
             wrap（换行）
             wrap-reverse(换行，第一行在下面）

#### 5、多行对齐方式（交叉轴）

     首先让项目多行（换行）
     align-content:flex-start(交叉轴的起点）
     flex-end(交叉轴的终点）
     center(中点） 、  space-between(两端对齐）、  space-around(两端等边距对齐）、  stretch(项目不设置高度    
     时占满整屏幕）

#### 项目的属性：

（1）、项目的顺序；

   order:可以有复制的整数，默认为0，数值越小越靠前；

（2）、项目的占比：放大占比

	flex-grow:
	默认值为0；即使有剩余空间也不放大，如果所有项目值都设为1，他们将对剩余空间等分，如果所有项目值都是1，有一  
	个是2，

（3）、项目的占比：缩小占比

	flex-shrink:不能填负值，默认值为1，
	空间不足时默认缩小，如果一个项目的flex-shrink属性为0；其他项目都为1；则空间不足时，前者不缩小；



## 三十、补充部分

### 常识概念

标签：以< >  <  />括起来的，大多数标记符必须成对使用；
属性：必须放在开始标签里，属性可以为标签提供多样化的特性。
元素：开始和结束标签联通包含在他们之间内容叫元素，内容叫元素的内容。

### html实体

html的实体：在html中有一些特殊符号属于HTML的关键字符，为了了让它在页面中显示，用html实体表示。



```

html实体：
&nbsp;(空格)  &lt;(小于号)  &gt;(大于号)  &quot;(引号)
&amp;(&)   &copy;(版权)
	
	
```

### a标签：

target:控制要跳转页面的打开位置；

target="_self"要跳转的页面在本窗口显示


target="_blank"要跳转的页面在新窗口显示


title:在该属性中写入鼠标移入时提示的内容


### img标签：

title:在该属性中写入鼠标移入时提示的内容


### 锚链接：可快速跳转

例如：<a href="#er"></a>此为链接入口
<a name="er"></a>此为标记锚点
<a href="#"></a>此标签可直接返回顶部


### input标签：

type：
name:用来交给服务器获取数据的
value:默认值
size:定义宽度；
maxlength:规定输入的最大字符数
disabled:规定空间是否可用
disabled="disabled"
readonly:规定空间的只读属性
readonly="readonly"
checked:默认选中


### 窗口针技术：

```
<fieldset><fieldset/>:将表单中的内容进行打包，双标签。
<legend><legend/>用来写打包内容的标题。

```

### label 标签


```

<label   fof="id名"> 

   里面为input标签，一般用在单选，注意应该加id名

<label/>

```

###  帧窗口技术
 
帧窗口技术：帧窗口应用帧技术可以使用户在同一浏览器中浏览不同的页面,不能与body共存。
实现方法：将浏览器切割成不同小窗口。




```
<frameset   cols="30%， 25%，25%，20%"    rows="30%， 25%，25%，20%"    frameborder="1"   border="2"  bordercolor="red" >

<frame   src="aa.html"   noresize="noresize">
<frame   src="aa.html2">
<frame    src="aa.html3">
<frame  src="aa.html4">


<frameset/>

<noframes> 您的浏览器不支持框架，请用最新的浏览器刷新界面。<noframes/> 

```




### iframe窗口帧技术 



iframe窗口帧技术：可以与body共存。

```
<iframe><iframe/>

```

属性：

src="aa.html"引入文件的路径。
frameborder="0"是否显示边框。
width="300"  height="300"设置帧窗口的宽度和高度。
scrolling="auto"用来设置滚动条
scrolling="yes"显示滚动条

scrolling="no"不显示滚动条



## 三十一、css的引入方法：

1、外部引入法：用link标签引入，在herf里面写入路径。

2、嵌入样式表：写在header中，用style双标签将样式包起来。

3、行内样式：给标签添加一个style属性，在该属性里写，要用引号引起来，样式和在css中的写法一样。

4、导入样式表：@import  url(base.css);将一个css文件导入另一个css文件中，

              url填将要导入文件的路径，一般用它导入base.css。


优先级：行内最高，在外部样式和嵌入样式中，那个离元素进，哪个优先级高。


## 三十二、属性选择器

1、[class]{ } 匹配定义了class属性的元素。

   [href]

2、[class="box1]{ } 匹配定义了属性为class，属性值为box1的元素。

3、[class^="b"]{ } 匹配属性为class，属性值以b开头的元素。

4、[class$="1"]{ } 匹配属性为class，属性值以1结尾的元素。

5、[class*="a"]{ } 匹配属性为class，属性值包含a的元素。


5、[class~="box"]{ } 匹配属性为class，属性值包含单词box的元素。(波浪线在中间）

6、[class|="box"]{ } 匹配属性为class，属性值包含连字符，并且属性值中以box开头的元素。

7、:root{} 匹配根元素  

8、input:enabled{}    选中input控件中可用的元素  

9、input:disabled{}     选中input控件中不可用的元素  disabled="disabled"

10、input:checked{}  匹配元素选中的状态，只用于单选按钮和复 选框                      

11、 ：：selection{}  匹配元素被鼠标选取的部分，只能作用少量的css属性    color  background   outline等

12、：empty{}匹配不包含子节点的元素

13、：only-child{}匹配作为唯一孩子的子元素

14、提高优先级的方法：在属性值后加！important;

15、交叉选择器：div.box{} 首先是div,其次是.box;

### 优先级顺序：

  ！importan>行内样式>交叉选择器和后代>ID选择器>类选择器>标记选择器>通用选择器>浏览器标签预定义样式>继承样式。

###  css两个属性：
  1、继承性：后代元素会继承父辈元素的一些样式。
  2、叠加性：同一个元素可以被多个元素指代，

###  伪类与伪元素

  伪类：选定的是元素，选定的是元素动态变化过程。
  伪元素：选定的是内容，对内容进行改变。

### 选择器优先级判断方法：

  style——a;如果有就为1，否则为0；
  id——b;值为id的数量；
  类名和伪类以及属性选择器的数量——c;
  后代选择期和伪元素的数量——d;
  通用选择器的数量——e;
  依次比较abcde的大小，




## 三十三、利用本地服务器进行真机测试


1、手机和电脑连到同一路由器下

2、安装 wampserver  绿色

3、将文件放到wamp文件夹下的www文件夹中

4、找到本机ip  用cmd命令

5、输入ipconfig 回车

6、找到ipv4  就是本机的ip



7、用手机浏览器访问电脑ip

8、找到相应的网页


## 三十四、移动端12中布局方式


1、列表式  教师列表

2、陈列式  天猫

3、九宫格  支付宝

4、选项卡   微信“朋友圈”


5、旋转木马式   轮播图


6、行为扩展式   和QQ里面联系人一样


7、对面版  一边导航一边详情


8、图表式  上面是图，下面是表


9、抽屉式  点击后从左边滑出 qq


10、超级菜单式   点开后有很多要刷新的东西


11、弹出式  弹出一个窗口

12、图片轮盘式  天猫有一栏   图很多一排放不下  但不换行


## 三十五、文本段落：

1、em相对于父元素的字体大小的单位
2、首行缩进：text-indent:2em;
3、设置字间距：letter-spacing:1em;(也可以设置为像素）
4、大小写转换：text-transform:none(无转化） uppercase(将小写转化成大写）  lowercase（将大写转化成小写）   capitalize(将每个单词的首字母转化成大写）
5、垂直居中：对行内块标签设置的，行内块标签默认状态下相对于基线对齐


        ```

                 vertical-align:top相对于顶线

                bottom相对于底线对齐

                middle  相对于文字的中线对齐

                baseline相对于文字的基线对齐

               顶线、中线、基线、底线（默认为基线）


         ```
         

## 三十六、隐藏属性


### overflow属性：

属性值：

hiddle：子元素超出父元素的尺寸，可对超出部分隐藏，加在父元素上。
auto:超出后出现滚动条：
visible：超出部分显示
scroll：  始终出现滚动条


### visibility属性：

属性值：

visible:显示元素
hiddle:隐藏元素


### opacity属性：

opacity:通过不透明度为0隐藏该元素


### disply、visibility、opacity隐藏元素的区别

disply:none元素不可见且不占据空间

visibility:hiddle 元素不可见，但占据空间

opacity:0;元素不可见但已然占据空间

 
## 三十七、IE6下的bag问题

（1）、img在IE6下有边框：

   问题描述：a标签包图片会出现难看的边框：

   解决办法：

   ```
   img{

     border:0;
   }

   ```


  (2)、IE6的双倍边距问题：

  问题描述：当给元素浮动后，加左边距时，ie6出现双倍边距；

  解决方法：加disply:inline;


  （3）、ie6不支持固定定位：

  问题：IE6不支持固定定位；（利用绝对定位模拟固定定位）

  解决：

  ```
  css
  
  选择器{
      width:200px;height:200px;background:red;
      position:fixed;bottom:50px;right:50px;
      *position:absolute;
      *top:expression(eval(document.documentElement.scrollTop+200));
  }
  *html{
      background-image:url(blank:about);
      background-attachment:absolute;
  }

  ```
