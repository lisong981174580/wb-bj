---
title: JavaScript语言——函数篇
tags: 李松,2017.4.15
grammar_cjkRuby: true
---


## 一、全局变量与局部变量
 var:全局变量
 let:局部变量
#### 重要特点：
1、var 关键字可以提升变量
2、let与const  
 （1）、如果在块级作用域中存在let或者const，他所声明的变量就会绑定该区域，并不会受外部的影响
 （2）、在同一个作用的区域中，let与const所声明的变量不能重复声明,在不同的区域是可以的。
 （3）、在同一作用域中若引用let或const所声明的变量必须在其声明后使用。
3、let或const不会实现提升变量

```
console.log(a);
var a=10;
不会报错

console.log(a);
let  a=10;
报错

```

## 二、函数的概念

函数:将某一具有特定功能的代码集合起来，可以重复使用的代码块。
#### 优点：
1、使程序更加简介
2、逻辑行更强
3、调用更方便
4、维护更容易

## 三、怎样创建函数

#### （1）、通过字面量创建函数

```

var aa=function([参数1],[参数2],...){

	函数体
	return返回值
}

```


例子：

``` 
var aa=function(){

	alert("我是字面量");
}
// 等号后面的函数称为匿名函数

 aa();

```


#### （2）、通过关键字来创建函数

```
function 关键字（[参数1],[参数2],...）{


	//	函数体
// 	return返回值
}

```

例子：

```
function aa(){

	alert("我是关键字");
}

aa();

```

#### （3）、通过对象的方式创建函数

```
var aa=new Function([参数1],[参数2],...,函数体);
var aa=new Function(alert(23));

```

## 四、函数的调用方式

#### （1）、字面量或者关键字加（）;
#### （2）、函数的自调用;

```
 (function(){

 	alert("函数的自调用");
 }) ();

```

#### （3）、事件后触发函数

```
<style>

.box{

	width: 100px;
	height: 200px;
	background: red;
}

</style>
<body>
	
	<div class="box"  onclick="javascript:aa()"; ></div>

</body>


<script>

function aa(){

	alert("事件触发的函数,我是.box");
}

</script>

```

## 五、声明与调用函数时应注意的问题

（1）、如果两处函数命名相同，则后面的会覆盖前面的函数;

```
  function bb(){

  	alert("这是第1个函数");
  }

  function bb(){

  	alert("这是第2个函数");
  }
  bb();
```

（2）、以基本语法声明的函数，会在页面载入的时候提前解析到内存中，以便调用。所以可以在函数前面调用，但是以字面量形式命名的函数，会在执行到他的时候，才进行赋值，所以只能在函数的后面调用。

```  

    var  cc=function(){

 	alert("这是字面量调用的函数");
   }

  alert(cc());

  可以实现

   cc();
  
    var  cc=function(){
  
   	alert("这是字面量调用的函数");
   }

   不可以实现
   
```

（3）、在不同的script块中，因为浏览器解析的时候是分块解析的，所以前面的块不能调用后面块的函数，所以在不同的块之间调用函数的时候，应先定义后调用。


## 六、参数

形参：在定义函数的时候，函数括号中定义的变量叫做形参。用来接收实参的。
实参：调用函数的时候，在括号中传入的变量或值叫做实参。用于传递给形参,实参的类型可以是任意的。

```
function typeOf(a){

alert(a);
alert(typeof a);
}

typeOf(123);
typeOf(null);
typeOf(undefined);
typeOf("字符串");
typeOf(true);
typeOf(function(){
	alert(2);
});

其中：a为形参;数字2为实参;

```
### 重要特点：

（1）、当传入的实参与形参数量相同时候，会一一对应。

```
function aa(a,b){

	alert(a);
	alert(b);
}

aa(38,"实参");

```
（2）、当传入的实参数量小于形参的数量，他会默认赋值为undefined;

```
function aa(a,b){

	alert(a);
	alert(b);
}

aa(38);

```

（3）、当你传入的实参数量大于形参的数量，我们通过arguments获取它所有的参数信息。

```
function aa(a,b){

	alert(a);
	alert(b);
	console.log(arguments);//通过arguments获取它所有的参数信息。
	alert(arguments.length);//通过arguments.length获取参数的个数。
	alert(arguments[4]);//实参的下标是从0开始计数的，通过arguments[4]获取某一个。
	alert(arguments.callee);//获取函数本身的信息
}

aa(38,34,56,78,90);

```

## 七、函数的重载：

同一个函数因为参数的类型或数量不同，可以对多个函数实现，每种实现对应一个函数体；

```
 function argunment(a,b){
 	if(arguments.length==1){

 		alert("参数只有a;他的值为"+a);

 	}else if(arguments.length==2){
 		alert("参数a的值为"+a+"参数b的值为"+b);
 	}else{
 		alert("参数值超过上限");
 	}
 }

  argunment(12);

```


测试数据的类型

```
function type(aa){

    if(typeof aa=='number'){

    	alert('这是数值型');
    }else if(typeof aa=='string'){
    	alert('这是字符串型');
    }else if(typeof aa==' boolean'){
    	alert('这是布尔型');
    }else if(typeof aa==' null'){
    	alert('这是对象');
    }else if(typeof aa=='  undefined '){
    	alert('这是 undefined ');
    }else if(typeof aa=='  symbel '){
    	alert('这是 symbel ');
    }else{

    	alert('这是引用类型 ');
    }          

  }

  type(23);

  ```



## 八、函数的返回值 return

#### 1、停止执行并跳出当前函数

```
   function aa(){

    return;
   	alert("aa函数");
   }

   aa();
```

#### 2、一个函数中存在多个return，只有一个return执行。

```
    function bb(a){

        if(a>0){
        	alert(a);
        	return;
        }

        if(a<0){
        	alert(a);
        	return;
        }
   }

   bb(3);

```
###  return语句用法总结：

1、在return语句后面的函数体内所有内容都不会输出；
2、在函数体内可以有多个return语句，但是只会执行一个。
3、返回值：

（1）、返回值可以是任意的数据类型。

```
		

            function nn(){

            	// return "这是字符串型";
            	// return null;
            	// return undefined;
            }

          alert(nn());
```

（2）、只能返回一个返回值，并且是最后一个值

```
		
              function nn(){

            	return "这是字符串型" ,null,undefined;
            	
            }

            alert(nn());
```

（3）、如果函数没有返回值，那么这个函数的值就会自动赋值为undefined;

```
               function nn(){

            	return ;
            	
            }

            alert(nn());
```
## 九、作用域

#### （1）、作用域：指的是一段代码的作用范围；
#### （2）、全局变量：在页面中任何地方都能访问到的变量，拥有全局的作用域。
           a.函数最外层定义的变量
           b、没有定义直接赋值的变量，拥有全局属性
#### （3）、局部变量：只能在固定的代码片段（函数片段中）中访问到；
            a.函数内部定义的变量，就是局部变量。
            b.参数也是局部变量。
#### （4）、作用域链：
我们可以把所有有作用域看成是一个链条链接起来的，这样能使变量和函数能够有序有机的进行运行。
1、宿主环境
2、执行环境
执行环境决定了变量和函数的作用域
 a.全局环境
 b.函数环境

## 十、javascript 预解析顺序

1、script块依次解析
2、解析代码运行的环境（最后eval字符串解析)
3、对标识符（关键字）（var function）进行解析，解析到相应的环境下。
4、如果还有script 块，再按照上面的步骤依次解析。


## 十一、 回调函数：
 
  当一个函数指针，作为另一个函数的参数，当他被调用后的时候，我们称之为回调函数。
  
  实现两个数相加或相减的例子：
  
  
   ```
     function jia(num1,num2){

     	return num1+num2;
      }

      function jian(num1,num2){

      	return  num1-num2;
      } 

      function  jisuan(num1,num2,fun){

      	return fun(num1,num2);
      } 

      alert(jisuan(22,10,jia));
```

## 十二、递归函数
      
      在函数内部间接或直接的调用函数本身，递归函数必须有一个终止条件。
      
 ```
      function tt(num){

      	if(num>1){
      		tt(--num);
      	}
      	document.write(num);
      }

      tt(5);   

      function jiecheng(num){

          if(num==0){

          return num=0;

          }else if(num==1){

          	return num=1;
          }else if(num>1){

          	return num*jiecheng(--num);
          }else{

            return  "数值不符合情况";
          }
     }  

    alert( jiecheng(0));
 
```

##   十三、闭包函数

   一个函数中嵌套另一个函数
    函数对象通过作用域链关联起来，并且变量保存在函数的作用域内。
    
    
```

    function aa(){

    	var bb=prompt("请输入一个数",0);
    	return function(){
    		return bb;
    	}
    }
   
     var cc=aa();
     alert("这个数是"+cc());
     console.log(cc);
 ```
      
      
## 十四、内置顶层函数

1. escape()  将非字母、数字字符进行编
 
例子：
```
     var pp=escape('有一颗善良的心');
     console.log(pp);
     var PP2=unescape('%u6709%u4E00%u9897%u5584%u826F%u7684%u5FC3');
     alert(PP2);
     
     function aa2(a){
      alert(Number(a));
     }
     aa2('123');  //null为0 undefined 为NaN
```
2. unescape()对编码的字符串进行解码

例子：

3. Number() 转化成数值类型

#### 注意：

```
    Number()  转化成数值类型
    a.如果是布尔值，false为0，true为1；
    b.如果是数字，转换成本身，将无意义的后导0去掉。
    c.如果是null转化为0；
    d.如果是undefined转化为 NaN  not a number 
    e.如果是字符串
    1.如果字符串当中只有数字，转化为10进制（忽略前导0和后导0）
    2.如果是有效规范的浮点型，转化为浮点值（忽略前导0和后导0）
    3.如果是空字符串，则转化为0；
    4.如果是其他的值，返回NaN;

 ``` 
 
4. String() 转换成字符串类型


#### 注意：

```
    String(参数)  转化成字符串类型
    可以将任何类型转化为字符串
    -null和undefined;也都会转化为字符串，分别为null和undefined
    -布尔类型：会返回true和false
    -数值类型：本身字符串
```    
5. Boolean() 转换成布尔类型

#### 注意：

```    
    Boolean() 转换成布尔类型
    -转化为假：""、0、NaN、undefined、false、null
    -其他全部都转化为真
```  
6. parseInt() 将字符串转化成整型

#### 注意：
```   
    parseInt() 将字符串转化成整型，直解析数字部分
    a.如果一个字符串只包含数字，则以十进制的方式转化成整型
    b.他会自动忽略空格字符串前面空格；字符串前面第一个字符不是空格，数字，-，返回NaN;
        参数一：八进制，0 后面的数字不超过7；十进制 0x；十六进制 0-9  a-f;
        参数二：控制解析模式2-32；
```

例子：


```
    function aa3(a,b){
      alert(parseInt(a,b));
     }
     aa3(11,8);//该程序可以实现八进制转换，如将十进制数11输出为八进制
```
7. parseFloat() 转化成小数

#### 注意：
```
    parseFloat() 转化成小数
    a.字符串当中，只有第一个有效，其他的都是无效的
    b.如果字符串是一个有效的整数，他返回的是整数，不会返回浮点型。
```   

例子：

```  
    function aa4(a){
      alert(parseFloat(a));
     }
     aa4("11.4522444445","12");
```
8. isNaN()  判断一个数能否转化为数值类型

#### 注意：  不是数值类型返回真，否则返回假

例子：


```     
      function aa4(a){
        alert(isNaN(a));
     }
      aa4(11);
```

9. isFinite()是否为有穷数

#### 注意：有穷为真，无穷为假

例子：

```
   
   
     function aa5(a){
        alert(isFinite(a));
     }
      aa5(23e+45);
``` 

##  十五、隐式转换：
   
 1.算数运算符类  + -  *   /  %;
 
-  如果操作数不是数值，将隐式的调用Numbel()函数，按照这个函数的转化规则进行转换。
   如果转换不成功，整个表达式返回NaN
-  如果操作数都是数值，直接进行相加；任何数据类型和字符串相加，都是字符串型，然后返回他们拼接的结果
   如果操作数值为布尔值，那么进行Numbel()转换，false为0，true为1，然后相加。    
   
2.语句类

-  if语句和三元表达式里面的表达式会隐式的调用Boolean()函数，按照这个函数的转换规则，转换为相应的布尔值。

例子：

 ```
        if(表达式)｛

          ｝else{

          }

          var 变量=Boolean expression?真值：假值

          while(){


          }
```   
  
 

  



