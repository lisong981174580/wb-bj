---
title: JavaScript—数组篇
tags: 李松,2017.4.17
grammar_cjkRuby: true
---

## 一、数组

1.  是一个可以存储一组或一系列相关数据的容器。
2.  为什么要使用数组？
- 解决大量相关数据的存储和使用的问题。
- 便于程序的开发和维护。


## 二、 数组的创建方式：
    
1.通过对象的方式创建。
```
var arr=new Array();
alert(typeof arr);

```
2.隐式创建
```
var arr1=[];
alert(typeof arr1);
```

## 三、数组的赋值方式

1.给通过对象创建的数组进行赋值
- 声明后进行赋值
```
var arr=Array();
arr[0]=12;
arr[1]='aa';
arr[2]='cc';
console.log(arr);

```
- 声明的同时进行元素添加

```
var arr1=new Array(12,34,'aa','45','huahua');
alert(arr1);

```
2.给通过隐式创建的数组添加元素
- 声明后进行元素的添加
```
var arr3=[];
arr3[0]='23';
arr3[1]='dd';
arr3[2]='ee';
alert(arr3); 

```
- 声明的同时进行元素的添加
```
var arr4=[12,'ss',34,56,'ff'];
alert(arr4);

```
## 四、数组元素的获取

1.  通过下表获取单个元素，下表从0开始的
```
var arr4=[12,'ss',34,56,'ff'];
alert(arr1[2]); 获取第三个元素
alert(arr.length);获取元素的个数
alert(arr[arr.length-1];数组中的最后一个元素


```


## 五、数组的遍历：
初值：
var arr4=[12,'ss',34,56,'ff'];

1. 第一种方式  通过for循环进行遍历
```
for(var i=0;i<arr4.length;i++){

alert(arr4[i]);
}

```

2.第二种方式  通过while循环进行遍历
```
var j=0;
while(j<arr4.length){

alert(arr4[j]);
j++;

}

```

3. 第三种方式  for  in 进行循环

```

for(var i in arr4){

   alert(arr4[i]);
}

```

## 六、二维数组和三维数组

 ###  1. 二维数组
  
```         
var newarr=[[1,2],[23,34],['ssd','sddd']];

var aa=newarr[0][0];
alert(aa);

```
#### 二维数组的遍历方式
```
for(var i=0;i<newarr.length;i++){

for(var j=0;j<newarr[i].length;j++){

console.log(newarr[i][j]);
}

}

```

### 2.三维数组
```
         
var  arr3=[  [ [23,45], [34,67] ]  ,  [ ['33','sddf'], ['gfggf','sdd'] ]   ];

```

#### 三维数组的遍历

```
for(var i=0;i<arr3.length;i++){

 for(var j=0;j<arr3[i].length;j++){

    for(var x=0;x<arr3[i][j].length;x++){

      console.log(arr3[i][j][x]);
    }
  
 }

}

```

##  七、例子


###  1.判断一维数组中元素的最大值

方法一：
          
```
  var arr=[12,34,67,444,67,3,4,7,8];

  var max;

    // max=0;
    max=arr[0];
  for(var i=0;i<arr.length;i++){

     // max=max>arr[i]?max:arr[i];
     // console.log(max);


      if(max<arr[i]){

         max=arr[i];
       }
 
  }

  alert(max);
  
  ```
  
  方法二：封装函数
  
  ```
   var arr=[12,34,67,444,67,3,4,7,8];

   function  arrMax(aa){

	   var  arrMax=aa[0];
	   for(var i=0;i<aa.length;i++){

		   if(arrMax<aa[i]){

			   arrMax=aa[i];
		   }
	   }

	   return arrMax;
   }


   alert(arrMax(arr));

```
  
  
  ### 2、冒泡排序
  
  方法一：
  
```

var arr=[12,34,67,444,67,3,4,7,8];
var temp;

for(var i=0;i<arr.length;i++){

   for(var j=i+1;j<arr.length;j++){

    if(arr[i]>arr[j]){
   
       temp=arr[i];
       arr[i]=arr[j];
       arr[j]=temp;

     }

  }

}

alert(arr);

```

方法二：封装函数

```
   var arr=[12,34,67,444,67,3,4,7,8];
   function  paiXu(aa) {
        var temp;
       for(var i=0;i<aa.length;i++){
           for(var j=i+1;j<aa.length;j++){

               if(aa[i]>aa[j]){

                   temp=aa[i];
                   aa[i]=aa[j];
                   aa[j]=temp;
               }
           }

       }

       return  aa;

   }

alert( paiXu(arr));
```

方法三：正反排序


```

var arr=[12,34,67,444,67,3,4,7,8];
function  paiXu1(aa ,type) {
    var type=type ||  'asc';
    var temp;
    for(var i=0;i<aa.length;i++){

                for(var j=i+1;j<aa.length;j++){

                      if(type=='asc'){

                            if(aa[i]>aa[j]){

                                temp=aa[i];
                                aa[i]=aa[j];
                                aa[j]=temp;
                            }

                      }else if(type=='desc'){
                                if(aa[i]<aa[j]){

                                    temp=aa[i];
                                    aa[i]=aa[j];
                                    aa[j]=temp;
                                }
                        }
                }

    }

    return  aa;

}

alert( paiXu1(arr ));

```


### 3、去重复

方法一：

```
var  arr=[1,33,3,33,33,56,787,56] ;//去重复；
var arr1=[];
var h=0;
for(var i=0;i<arr.length;i++){

	for(var j=i+1;j<arr.length;j++){

		if(arr[i]==arr[j]){


			arr[j]=null;

		}
	}

	if(arr[i]!==null){

		arr1[h]=arr[i];
		h++;
	}

}
alert(arr1);

```

方法二：封装函数


```
var  arr=[1,33,3,33,33,56,787,56] ;//去重复；
var  newarr=[];
for(var i=0;i<arr.length;i++){

	if(quchong(arr[i], newarr)){

		newarr[newarr.length]=arr[i];
	}
}
alert(newarr);

function  quchong(a , bb){

	 for(var j=0;j<bb.length;j++){

		 if(a==bb[j]){

			 return false;
		 }
	 }

	 return  true;
 }
```

### 4、取出元素

```

var  arr2=[34,56,78,45,88,66,55,77];//把里面大于60的数组取出来组成一个新数组。
var arr3=[];
var k=0;
for(var i=0;i<arr2.length;i++){

	if(arr2[i]>60){
	  arr3[k]=arr2[i];
	  k++;
	}
}
alert(arr3);
```

### 5、取出二维数组的最大值和最小值


```
var  arr3=[[23,45,67,22],[34,78,67,33],[34,12,34,22]];//取出二维数组的最大值和最小值。
var max=arr3[0][0];
var min=arr3[0][0];
for(var i=0;i<arr3.length;i++){

	for(var j=0;j<arr3[i].length;j++){

		 if(max<arr3[i][j]){

			 max=arr3[i][j];
		 }
		if(min>arr3[i][j]){
			min=arr3[i][j];
		}

	}
}


alert("最大值是"+max+",最小值是"+min+" ");

```

### 6、把里面所有的字符串和布尔值取出组成一个新数组

```
var  arr4=['123','wo',false,true,123,'hao',null,undefined];//把里面所有的字符串和布尔值取出组成一个新数组。
function typeOf(aa){
	return  typeof(aa);
}
var arr5=[];
var k=0;
	for(var i=1;i<arr4.length;i++){
         if(typeOf(arr4[i])=="boolean"||typeOf(arr4[i])=="string" ){

			 arr5[k] =arr4[i];
			 k++;

		 }

	}
	alert(arr5);

```

### 7、取出二维数组中长度最长的数组


```

var arr=[0,[23,45],90,[88,67,656,44,44,44,33],[22,22]];	//取出最长的数组
var max=[];
	for(var i=0;i<arr.length;i++){

		if(typeof arr[i]=='object' && arr[i]!=null){

			if(arr[i].length>max.length){

				max=arr[i];
			}
		}
	}

	alert(max);
```

###  8、去空

方法一：

```
var arr=[23,23,56, , , ,45,66,88,99,'aa','44','hhj'];
var newarr=[];


for(var i=0;i<arr.length;i++){

    if(arr[i]!=null){

        newarr[newarr.length]=arr[i];
    }
}
alert(newarr);

```

方法二：封装函数

```
var arr=[23,23,56, , , ,45,66,88,99,'aa','44','hhj'];

function  qukong(aa) {

    var newarr=[];
    for(var i=0;i<aa.length;i++){

        if(aa[i]!=null){

           newarr[newarr.length]=aa[i];
        }
    }

return  newarr;

}

alert(qukong(arr));

```

###  9、给数组后面添加多个元素

```
 var  arr2=[34,56,78,45,88,66,55,77];	//给数组后面添加多个元素

function  push( ){

    for(var i=1;i<arguments.length;i++){

      arguments[0][arguments[0].length]=arguments[i];
}
    return  arguments[0];
}
    push(arr2,'aa','bb',12 );
    alert(arr2);

```
### 10、给数组前面添加多个元素

方法一：

```

var  arr3=[34,56,78,45,88,66,55,77];//给数组前面添加多个元素

    function  unshift( ) {

        for(var i=1;i<arguments.length;i++){

            arguments[0].length++;
            for(var j=1;j<arguments[0].length;j++){

                    arguments[0][arguments[0].length-j]=arguments[0][arguments[0].length-j-1];


             }

            arguments[0][0]=arguments[arguments.length-i];
        }

    }

  unshift(arr3,22,25);

   alert(arr3);

```

方法二：

```
var  arr3=[34,56,78,45,88,66,55,77];//给数组前面添加多个元素

function  unshift( ) {

     var newarr=[];
    for(var i=1;i<arguments.length;i++){

       newarr[newarr.length]=arguments[i];

    }
    for(var j=0;j<arguments[0].length;j++){

        newarr[newarr.length]=arguments[0][j];
    }

    return  newarr;

}

alert(unshift(arr3, 22,34,12 ));
```

### 11、去除数组最后一个元素

```
var  arr=[34,56,78,45,88,66,55,77];//去除数组最后一个元素

function  pop(a){

    var last=a[a.length-1];
    a.length=a.length-1;
}
    pop(arr);
   alert(arr);
```
### 12、去除数组第一个元素

```
var  arr=[34,56,78,45,88,66,55,77];//去除数组第一个元素

    function shift(bb){

    var first=bb[0];
        for(var i=0;i<bb.length;i++){

            bb[i]=bb[i+1];
        }
        bb.length=bb.length-1;
}

    shift(arr);
    alert(arr);
    
 ```   
 
 
 ### 13、十行十列表格函数的封装
 
 ```
function biaoge(a,b){
 var bg;
 var  str="<table   border='1px'  cellpadding='10'  align='center'  cellspacing='0'>";

 for(var i=1;i<=a;i++){

         if(i%2!==0){

            bg="red";
          }else{

            bg="green";
          }

     str+="<tr  bgcolor="+bg+">";


    for(var j=1;j<=b;j++){


      str+="<td  align='center'   > 第"+i+"行<br>第"+j+"列  </td>";

     
        }

          str+="</tr>";
}


  str+="</table>";

  document.write(str);

 }

 biaoge(10,10);

 ```
 
 ### 14、金字塔的封装
 
 ```
 function jinzita(a,b){

  var xing=a;
  document.write("<p align='center'>");
   for(var i=0;i<b;i++){

       for(var j=0;j<=i;j++){
            document.write(`&nbsp ${xing} &nbsp`);
       }
      document.write("<br>");
   }
      document.write("</p>");

 }

 jinzita("金字塔",10);
```
 
 ### 15、选出100-1000的水仙花数
 
```
   var hua=[];

   for(var i=100;i<1000;i++){
   

          var  a=parseInt(i/100);
          var  b=parseInt((i%100)/10); 
          var  c=i%10;

         if(i==a*a*a+b*b*b+c*c*c){

             console.log(hua.length);
         	 hua[hua.length]=i;

         }

   }

     alert(hua);



```