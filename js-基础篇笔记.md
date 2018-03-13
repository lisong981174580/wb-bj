---
title: JavaScrip语言—基础篇
tags: 李松,2017、4、10,
grammar_cjkRuby: true
---
## 一、概念

### 概念：javascript基于事件和对象驱动的松散型语言。
### 特点：
1、基于对象的一种语言
2、松散型、弱类型
3、由宿主对象（浏览器）进行解析
### 内容：
1、数据类型、运算符、数组、函数等。
2、BOM 浏览器  browser  object  Model
3、DOM  DOCUMENT  OBJECT  Model

### 用处：
1、用于数据验证
2、将动态的效果添加到内容中
3、还可以对html元素进行读写的操作
4、可以响应事件
5、可以创建cookie（涉及到登录注册，储存部分信息）
6、模拟动画
7、检测我们的浏览器


##  二、输出方式


### 位置：写在script标签对中

1、输入框： var aa=prompt("请输入你的信息","姓名"); 
2、对话框： var  bb=confirm("你确定要退出吗？");
3、弹出框：alert(弹出信息);
4、输出到控制台：console.log("我是控制台");


## 三、引入方式

 1. 嵌入式：写在script标签中
 2. 外部引入
 3. 通过事件引入js代码
 4. 在超链接和重定向引入js代码

## 四、变量的命名方式

1、以$或下划线或英文字母开头，后面可以是数字、字母、$、下划线
2、不能以关键字和保留字命名

### javascript本身命名方式：

 1. 驼峰命名法：wuSiTong
 2. 首字母大写命名法  Object

### 如何声明变量

#### 变量：储存数据的容器
var aa=23;暂时将数据保存在里面

### 测试方法：alert(aa)；看是否出现
 console.log("我是控制台")   在控制台看

 let bb="我是bb变量"; 定义变量

 const  cc=34;  定义常量

### 规则：
1、先定义、后赋值
  var  bb;
  bb=56;
  
2、定义和赋值同时进行
var  a=23;

3、先定义多个变量，在声明中每个变量用逗号隔开：然后再进行赋值。

var a,b,c,cd;
cd=20;
a=12;
b=13;
alert(cd);


4、声明多个变量并同时赋值，用逗号隔开

var a=34,b=89,d=90;


### 注释方式：

1、单行
2、多行


## 五、数据类型

### 两大类：初始类型、引用类型

### （1）、初始类型

   一般储存在栈区：number、string、boolear、null、undefined、symbol
   栈区特点：字符长度是固定的，内存小，读取速度快
   
   typeof：用来测试数据类型，返回值是字符串，一元运算符

####  一、number型：

 1. number 数字、整型、浮点型或者是十进制、二进制（0b010101)、八进制（0O0777）、十六进制（0x08ff)

 2. 浏览器最大值： var max=Number .MAX_VALUE;
 3. 浏览器最小值： var min=Number .MIN_VALUE;
 4. e代表10的几次方


#### 二、string  字符串，

 用引号引起来的数据都称为字符串

##### 引号的规范性

 1. 单双引号的效率一样
 2. 不能交叉使用
 3. 可以嵌套使用
 
 
#### 三、 boolean 布尔值

只有两个值：true  false


#### 四、null  

用于初始化，清空数据，是一个什么都没有的空对象，相当于一个占位符，数据类型是object


#### 五、 undefined 未定义 

 声明一个变量并没有赋值的情况下，默认值是undefined；

#### 六、symbel型   

在我们对象的属性名中，一种是字符串型，另一种就是我们的symbol型，他是独一无二，并不会与其他属性名称产生冲突


### （2）、 引用类型

    一般放在堆区
    堆区特点：容量大、数据长度不固定、读取速度慢
   object 函数、数组
   测试函数时弹出的对象是function；


## 六、部分应用：

### （1）、鼠标点击效果

代码如下：


```
<body>
	
	 <div  onclick="javascript:alert('我是div' )"></div>

	 <a href="javascript:alert('我是div' )"> 123</a>

	 <form action="javascript:alert('重定向' )">
            
            <input type="submit">
           
	 </form>


</body>

```

##  七、运算符

### 1. 算术运算符 + —  *  /   %  **

#### 例子：

```
定义变量
var  a=10,b=30;
相加拼接字符串
alert(a+"+"+b+"="+(a+b));
科学计数法
alert(b**a);
相乘拼接字符串
alert(a+"×"+b+"="+(a*b));
模板字符：
alert(`${b}-${a}=${a-b}`);
文本对象:也可实现拼接字符窜
document.write("<p>这是p标签"+(a+b)+"</p>");
document.write("<div>我是div</div>");

模板字符
document.write(`<a href="">${a+b}</a>`);
document.write("<a href=''>这是p标签"+(a-b)+"</a>");

```



### 2、比较运算符   =  >  <  >=  <=  ==  ===  !=  !==
####  例子：
```
定义变量
var  a=10,b=40;
判断b>a是否为真  真为ture  假为 false 
alert(b>a);

如果字符串中的数字与常量值相等，则以下值为 ture,但===是不成立的

console.log("111"==111);

只和第一个字母相比较  此时值为false 
console.log("ces">"d");


true 值为 1 ,false 值为 0;

console.log(true>0);  true 1   false  0;

null是一个空对象，但值不等于0
console.log(null==0); /* false*/

undefined是一个空对象，但值不等于0
console.log(undefined==0);false



undefined 和 null都是空对象
console.log(undefined==null);  true


console.log("111"===111);false  必须一模一样

NaN是Numbel类型
console.log(typeof NaN);  Numbel

将字符串转化成数字
console.log(Number("111"));

特殊情况：
console.log(NaN===NaN);false
```
### 3、 赋值运算符  +=  *=  -=   %=  **=
 
 ```
 ++a 先自加，后运行
 a++  先运行，后加
 ```
###  4、逻辑运算符： &&与  ||或   ！非   

#### 注意：  ""    0  NaN  null  undefined  的布尔值都为false;

alert(Boolean(1)); ture

短路原则：&& ||


### 5、其他运算符：++  --  +正  - 负 
#### 注意：typeof  new  delete 称之为一元运算符 
#### 注意2：
  数值里面只有 0 和NaN  是 false;
  字符串里只有 空对象是  false;
  NaN  是Numbel型 但不是一个数

三元运算符：

样式：
var  ss=23?89:90;

测试：
alert(ss);
var  a=30;
var  b=40;

alert(a>b?"真的":"假的");

转化成ASCLL代码值代码：
 var  bb="a";
alert(bb.charCodeAt());




#### 例子：找出三个数的最大值和最小值


```
var  Num1=Number(prompt("请输入第一个数",0));

var  Num2=Number(prompt("请输入第二个数",0));

var  Num3=Number(prompt("请输入第三个数",0));

var max=(Num1>Num2?Num1:Num2)>Num3?(Num1>Num2?Num1:Num2):Num3 ,
    min=(Num1>Num2?Num2:Num1)>Num3?Num3:(Num1>Num2?Num2:Num1);

console.log( max,min);

```


## 八、JavaScript流程控制

1、流程：程序代码的执行顺序
2、流程控制：通过规定的语句让程序代码有条件的按一定方式执行。
3、顺序结构：按照书写顺序来执行，是程序中最基本的流程。
4、选择结构（分支结构、条件结构）：根据给定的条件有选择的执行相应语句。
5、循环结构：在给定的条件满足下，反复执行同一段代码。

### （1）单路分支：

  ```

    if(){

    }

  ```

例子：
```
var bb=Number(prompt("请输入数值",0));

alert(bb);

```


### （2）、双路分支 if语句

例子：
```

var kk=Number(prompt("请输入数值",0));

	if(kk>60){

		alert("成绩合格，你很棒");
	}else{
		alert("成绩不合格");
	}

```

### （3）、多路分支

例子：

```
var hh=Number(prompt("请输入数值",0));

if(hh==100){

	alert("满分，你太牛逼了，你是李松吧")
}else  if(hh>=90 &&  hh<100){

	alert("优秀")
}else  if(hh>=80 &&  hh<90){

	alert("良好")
}else  if(hh>=70&&  hh<80){

	alert("较好")
}else  if(hh>=60 &&  hh<70){

	alert("及格")
}else  if( hh<60){

	alert("不及格，唉不行，你是立航吧")
}

```


### （4）、嵌套分支

例子：

```
var jj=Number(prompt("请输入一个数",0));

if(jj>=60 && jj<100){

    if(jj>=60 && jj<70){
    	alert("及格");
    }else if(jj>=70 && jj<80){

    	alert("还行");
    }else  if(jj>=80  && jj<90){
    	alert("良好");
    }else {

    	alert("牛逼");
    }

}

```

### （5）、switch语句 

例子：

```
var  
     ll1=Number(prompt("请输入第一个数",0)),
     ll=prompt("请输入一个符号","+"),
     ll2=Number(prompt("请输入第二个数",0));

switch(ll){

  case "+":document.write(`${ll1}+${ll2}=${ll1+ll2}`);break;
  case "-":document.write(`${ll1}-${ll2}=${ll1-ll2}`);break;
  case "*":document.write(`${ll1}×${ll2}=${ll1*ll2}`);break;

  //引入字符串的方式：分别为1、模板字符法 2、拼接字符  3、字符串拼接
  case "/":document.write(`${ll1}÷${ll2}=${ll1/ll2}`);break;
  case "/" :document.write(ll1+"/"+ll2+"="+(ll1/ll2));break;
  case "%":document.write(""+ll1+" % "+ll2+" = "+ll1%ll2+" ");break;

  default:document.write("没有相关的符号");break;

}

```

### switch与if的区别

1、当判断某种范围的时候最好用if语句；当判断单个的时候用switch;
2、条件满足的情况下不可以重复，会发生不可预期的错误。




## 九、循环语句
### (1)、while循环:
 当条件满足的时候会一直循环，条件不满足时会退出循环。
	
	```
		var v=0;
		while(v<9){
			console.log("这是while循环");
			console.log(v);
			v++;
		}

	```
### (2)do{} while(表单式)

先最少执行一次，在进行条件的判断，如果满足则继续执行，如果不满足则退出。

```
var v2=91;

do{
console.log("这是do循环");
v2++;
console.log(v2);
}while(v2<1);

```

### （3）、for循环


例子：


```
 var  password;

 for(var i=0;i<3 &&  password!=="123" ;i++){

    if(i==0){
    	password=prompt("请输入密码",0);

    }else{

    	password=prompt("请再次输入密码",0);
    }
    
 }

 if( password==="123"){

 	alert("登录成功");
 }else{

 	alert("输入次数已到达上限");
 }

```


### for循环和while的区别

 1、for一般用于循环指定的次数
 2、while是根据条件的真假来判断，真的时候循环，假的时候退出.

### (4）、部分案例

#### 一、密码输入三次

方法一：

```
var password=prompt("请输入密码",0),a=0;

    while(a<2 && password!=="123"){

	        a++;
	        console.log(a);
	        password=prompt("请输入密码",0);
}

    if(password=="123"){
		
		    alert("登录成功");
}else{

	        alert("输入次数已到达上限");
}

```

方法二：

```
var a=0  ,password ;
do{
	 if(a==0){

	 	password=prompt("请输入密码",0);
	 }else{

	 	password=prompt("请再次输入密码",0);
	 }
	
    a++;

}while(a<3  && password!=="123" );

if(password=="123"){

	alert("登录成功");
}else{
	alert("输入次数已到达上限");
}

```


方法三：


```
  var  password;

  for(var i=0;i<3 &&  password!=="123" ;i++){

    if(i==0){
    	password=prompt("请输入密码",0);

    }else{

    	password=prompt("请再次输入密码",0);
    }
    
 }

 if( password==="123"){

 	alert("登录成功");
 }else{

 	alert("输入次数已到达上限");
 }

```

#### 二、偶数的和

```
 var num=0  ;
 for(var i=0;i<101;i++){

      if(i%2==0){

      	num+=i;
      }

    


 }

  alert("偶数的和="+num+" ");
```

#### 三、十行十列表格

方法一：

```
var bg;
document.write("<table  cellspacing='0' cellpadding='10' border='1'   align='center' >");

      for(var i=0;i<10;i++){

          if(i%2==0){

              var  bg="red";

              }else{

              var  bg='green';

              }

              document.write("<tr  bgcolor="+bg+">");

              for(var j=0;j<10;j++){

              document.write("<td  align='center'>第"+i+"行<br>第"+j+"列</td> ");

          }

          document.write("</tr>");

      }

document.write("</table>");

```

方法二：


```
 var bg;
 var  str="<table   border='1px'  cellpadding='10'  align='center'  cellspacing='0'>";

 for(var i=1;i<=10;i++){

         if(i%2!==0){

            bg="red";
          }else{

            bg="green";
          }

     str+="<tr  bgcolor="+bg+">";


    for(var j=1;j<=10;j++){


      str+="<td  align='center'   > 第"+i+"行<br>第"+j+"列  </td>";

     
        }

          str+="</tr>";
}


  str+="</table>";

  document.write(str);

```


#### 四、九九乘法表

```
 
   for(var i=1;i<10;i++){

       for(var j=1;j<=i;j++){

         // document.write("  "+i+" * "+j+" = "+i*j+" &nbsp;&nbsp;   ");

         // document.write(i+"*"+j+"="+i*j+"&nbsp;&nbsp;");
           
            document.write(`${i} × ${j}= ${i*j} &nbsp;&nbsp;   `);
           
           }

       document.write("<br>");
    }

```

#### 五、鸡兔同笼

鸡兔同笼，34只头，96只脚，鸡兔有几何？

```
  for(var i=0;i<34;i++){

  	 for(var j=0;j<34;j++){

        if(i+j==34 &&  2*i+4*j==96){

        	alert(`兔有${j}只,小鸡有${i}只`);
        }
   }
}

```

#### 六、操场问题

操场上有100多个学生，站成3排余1个，站成4排余2个，5排余3个，学生有多少？

```
for(var i=100;i<200;i++){
  
     if(i%3==1 &&  i%4==2  && i%5==3){

     	alert(i);
     }
 

}

```

#### 七、金字塔

方法一：

```
       var xing="*";
  document.write("<p align='center'>");
   for(var i=0;i<5;i++){

       for(var j=0;j<=i;j++){
            document.write(`&nbsp ${xing} &nbsp`);
       }
      document.write("<br>");
   }
      document.write("</p>");

```

方法二：


```
 document.write("");

	for(var i=0;i<10;i++ ){

    for(var j=0;j<=i;j++){


      document.write("* ");
    }

    document.write("");
  }

  
 document.write("");

```

## 十、字符串拼接

本节主要做回顾，以及对前面字符串拼接部分做一些总结：

```
  
  var b=3;
  var a=10;
  alert(a+b) ;            //13;
  第一种      alert(""+a+"+"+b+"="+(a+b)+" ")    //引号中中引入变量; "+a+"变量；其他+连接
  第二种      alert(a+"+"+b+"="+(a+b));         //变量加字符串，
  第三种      alert(`${a}+${b}=${a+b}`)  //模板字符   //10+3=13;  
  在字符串中书写行内样式  

  document.write("<div style='text-align:center'>"+a+"</div>") ;

  注意：如果外边是双引号，写css样式是用单引，
       如果外边是单引号，写css样式是用双引，

```

## 十一、break语句和continue语句
 break语句：满足条件后直接退出,跳出并终止循环
 continue:满足条件后不执行，而执行下面的语句，跳出并终止当前循环

```

for(var i=0;i<5;i++){

  for(var j=0;j<5;j++){

    if(j==2){

    	continue;
    }


   console.log(j);

  }

}

```



        
