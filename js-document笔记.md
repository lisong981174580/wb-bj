---
title: JavaScript—document篇
tags: 李松,2017.4.22
grammar_cjkRuby: true
---

##  一、概念

是window的一个子对象，常用来获取页面元素并操作该元素


## 二、属性

```
console.log(document.title); //显示标题

document.title="document"; //设置标题

console.log(document.URL)  ;//输出路径

```
## 三、方法

###  1、获取元素

#### （1）、通过标签名获取元素

```
var div1=document.getElementsByTagName('div');//通过标签名获取元素，然后返回给一个数组
console.log(div1);

var div2=document.getElementsByTagName('*');//获取页面中所有元素
console.log(div2);

```

#### （2）、通过类名选择元素

```
var div7=document.getElementsByClassName('box5');//通过类名选择元素，ie8以下浏览器不能用
console.log(div7);


```
#### （3）、通过name选择元素
```
var div3=document.getElementByName('box1');//通过name选择,ie8以下的浏览器只能获取表单元素
console.log(div3)

```
#### （4）、通过Id名选择元素


```
var div2=document.getElementById('box1');//通过Id名获取元素，如果有重复的Id则,js选的时候只能选一个
console.log(div2);

```

#### （5）、获取满足这个选择器的第一个元素
```

var div4=document.querySelector("#aa");//获取满足这个选择器的第一个元素，返回值为该元素，ie8以下浏览器不能用
console.log(div4);

```

#### （6）、获取满足这个选择器的所有元素

```
var div5=document.querySelectorAll(".box5");//获取满足这个选择器的所有元素，返回值为数组，ie8以下浏览器不能用
console.log(div5);


```
#### （7）、获取某个元素的子元素

```
var div1=document.getElementsByClassName('right')[0];
console.log(div1);

var div2=div1.getElementsByTagName('div');
console.log(div2);

```
#### （8）、获取某个元素的子元素 常用方法
```
var div5=document.querySelectorAll(".right   div");

  //获取满足这个选择器的所有元素，返回值为类名为right的子元素div（标签名）组成数组，ie8以下浏览器不能用

console.log(div5);


```

###  2、属性

#### （1）、获取元素的类名 .className

```
var div1=document.getElementsByTagName('div')[0];
console.log(div1.className);

```
#### （2）、添加css样式，为行内样式

```
var div7=document.getElementsByClassName('box5');
div7[0].style.width="200px";
div7[0].style.height="200px";
div7[0].style.background="blue";


```

#### （3）、onclick 鼠标点击

#### （4）、onmouseover  鼠标移入

#### （5）、onmouseout   鼠标移出

## 四、经典案例

### （1）功能：在任意浏览器中可以通过类名获取元素,消除ie8以下版本的兼容性问题


```
 function  getClass(sel,obj){

             //判断是否找子元素
             var obj=obj || document;
             var arr=[];
             //找到所有元素
             var all=obj.getElementsByTagName('*');
             //遍历所有元素
             for(var i=0;i<all.length;i++){
                   //获得所有元素类名
                   var str=all[i].className;
                   //判断类名是否满足条件    
                    if(  choose( str ,sel  ) ){

                       	   arr[arr.length]=all[i];
                    }

               }
             //返回符合的元素
             return arr;

       }



    
       // 判断类名是否满足条件
       function  choose(aa,bb  ){

            //先将字符串转化成数组，然后遍历它
       			var newarr=aa.split(" ");

       			for(var  i=0;i<newarr.length;i++){
                   //若遍历出来的类名有一个和条件相同则返回真
                  if(newarr[i]==bb){

                      	return  true;
                     
                      }

       			}

       			return false;
       			
       }

      //调用该函数找到类名为5的元素
      var div1=getClass("box5");
      console.log(div1);

       //调用该函数找到类名为5的元素的子元素zhezhao
      var newarr=getClass("zhezhao",div1[0]);  //想想传数组
      console.log(newarr);




```


### （2）功能：实现鼠标移入和选项卡效果

 鼠标移入效果
```
<script>

   // 鼠标移入效果

            //获取类名为box5的元素
            var box=document.getElementsByClassName('box5');
            //获取类名为zhezhao的元素
            var zhezhao=document.getElementsByClassName('zhezhao');

           //遍历box5的元素
           for(var i=0;i<box.length;i++){

                // 将每一遍的i值绑定到所遍历的那一次上
                box[i].index=i;
                
                // 鼠标移入效果
                box[i].onmouseover=function(){

              
              	zhezhao[this.index].style.width="100%";
              	zhezhao[this.index].style.height="100%";

                 }
                // 鼠标移出效果
                box[i].onmouseout=function(){

              
              	zhezhao[this.index].style.width="0%";
              	zhezhao[this.index].style.height="0%";

                }

            }

```
颜色选项卡

```
      //颜色选项卡


        //获取类名为left的所有标签名为div的子元素
        var dianji=document.querySelectorAll(".left div");
         //获取类名为right的所有标签名为div的子元素
        var xiaoguo=document.querySelectorAll(".right div");

        //遍历所有dianji,用局部变量，将变量绑定到每一次的循环上
        for(let i=0;i<dianji.length;i++){
           
                  //添加点击事件
  	              dianji[i].onclick=function(){

                       //首先让所有元素背景色为#eee 
  			               for(let j=0;j<dianji.length;j++){


  			               	   dianji[j].style.background="#eee";

  			               }

  			                //然后让点击的那个背景为#ccc
                        this.style.background="#ccc";


                       //首先让所有xiaoguo都不可见
                       for(let j=0;j<xiaoguo.length;j++){


  			               	  xiaoguo[j].style.display="none";


  			               }

                       //然后点击时让某个出现

  			              
                        xiaoguo[i].style.display="block";
                                
                  }   

        }
        
 </script>       

```

## 五、document用法

### （1）、获取元素后操作内容

a. innerHTML  获取所有html内容

b. innerText  只能获得文本，并且只能在IE 谷歌中使用

c. textContent  只能获得文本，并且只能在火狐  谷歌中使用


例子：
```
//通过id名获取元素赋值给aa;
var aa=document.getElementById('box');

//通过innerHTML属性给内容赋值
aa.innerHTML="我是优秀的共青团员";//对内容赋值

//弹出内容
alert(aa.innerHTML);//弹出内容  可以获得所有html内容

//innerText属性只能获得文本，并且只能在IE 谷歌中使用
alert(aa.innerText);//IE 谷歌  只获得文本

//textContent属性只能获得文本，并且只能在火狐  谷歌中使用
alert(aa.textContent);//火狐  谷歌  只获得文本

```
d.获取内容与给内容赋值（函数）

```


 function getText( ){
      
      if(arguments.length==2){

        arguments[0].innerHTML=arguments[1];
      	alert(arguments[0].innerHTML);
      }else{

      	alert(arguments[0].innerHTML);
      }

}


getText(aa); //获取内容
getText(aa,"李松");  //对内容赋值



```


### (2)、获取元素的样式    层级最高的

#### 注意：aa.style.width;  只能获得行内样式
#### a、window.getComputedStyle(aa,null)；ie不能用   谷歌、火狐能用

window是一个对象 上面有一个getComputedStyle方法（方法就是函数），调用时，传入两个参数，第一个参数
是元素对象,返回值还是一个对象，上面有所有当前的css样式

#### b、aa.currentStyle.width  在谷歌、火狐都中不能用    ie能用

```
//获得aa的css属性中的width
alert(window.getComputedStyle(aa,null).width);//ie不能用   谷歌、火狐能用

//获得aa的css属性中的width
alert(aa.currentStyle.width);//在谷歌、火狐都中不能用    ie能用


//只能获得行内样式
aa.style.width="400px";
console.log(aa.style.width);//只能获得行内样式

```

#### c、去除兼容型问题

```
function getStyle(obj,prop){
    if(obj.currentStyle==undefined){

    	return  window.getComputedStyle(obj,null)[prop];
    }else{

    	return obj.currentStyle[prop];
    }

}

console.log(getStyle(aa,"width"));


```

### (3)、对元素的属性进行操作

```
console.log(aa.id);//输出id名

aa.className="box1";//添加类名

console.log(aa.className);//输出类名


aa.ff="aa";//加在对象上，无法隐射到标签上

aa.setAttribute("gg","cc");//添加属性  gg="cc"  可以隐射到标签上  

console.log(aa.getAttribute("gg"));//获取属性

console.log(aa);




```

### (4)、对元素样式进项操作

#### a、第一种
```
aa.style.width="300px";
```
#### b、第二种：删掉中划线，下一个字母大写
```
aa.style.zIndex=3;
```
#### c、综合写法
```
aa.style.cssText="width:500px;height:500px;color:green;";
```
#### 对象属性值的获取,以下方式只能获取行内样式

```
aa.style.width

```


### (5)、批量修改

```
//先预定义好一个css样式，使用的是类名gg；
aa.className="gg";//然后将类名gg定义的样式赋值给元素aa;

//先预定义好一个css样式，使用的是id名cc；
bb.id="cc";//然后将id名定义的样式赋值给元素aa;

```

### （6）、属性的追加与删除

```
//获取元素
var hh=document.getElementsByClassName("box5")[0];

//追加css属性
 hh.classList.add("box6"); 
 
//删除css属性
hh.classList.remove("box6");

//点击效果
hh.onclick=function(){

hh.classList.toggle("box6");//取反

hh.classList.toggle("box6" ,true);//强制添加

hh.classList.toggle("box6",false);//强制删除

}

```
