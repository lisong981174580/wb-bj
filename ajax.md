---
title: ajax 
tags: 李松,2017.6.13
grammar_cjkRuby: true
---

### 一、ajax执行流程（异步js) //7.0.0.1 (localhost)|
*   取数据
*   创建对象  xml
*   打开请求Xml.open('get','data.txt',true);   true表示是否异步  get表示环境   中间为路径
*   发送请求  xml.send();
*   添加异步监听事件（数据是否能够成功获取）
*   xml.onreadystatechange=function(){ }
```
 /*创建一个对象*/
    let xml=new XMLHttpRequest();
    /*打开请求*/
    xml.open('get','data.txt',true);
    /*发送请求*/
    xml.send();
    //localhost  www
    //监测事件
    xml.onreadystatechange=function(){
    //判断是否开始帮你找
        if(xml.readyState==4){
    //找到后执行的任务
            if(xml.status==200){
    //将数据输出到控制台
                console.log(xml.responseText);
            }
        }
    }
```
### 二、命令行语句
* node -v  程序是否安装上  安装后显示版本号
* npm -v   安装包

### 三、PHP
#### 规范：
* 只能在服务器环境下运行
* 数据可以写成两行
* 数据不需要声明
* 可以嵌套html，但不能被html嵌套

#### 重要属性
>指定你的页面是utf-8编码。
```
header("content-type:text/html;charset=utf8");

```
>echo :输出一个或多个字符串；

```
$arr=['name'=>'zhangsan','arg'=>18];
//echo $arr['name'];  //输出数组中的某个元素


$arr=['name'=>'zhangsan','arg'=>18];
echo json_encode($arr);//以json格式输出数组

$a=10;
echo $a;   //输出变量

```


>打印数组及变量
```
$arr=['name'=>'zhangsan','arg'=>18];
print_r($arr);//打印数组


$a=10;
print_r($a);//打印变量
```

>  此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。

```
$a=10;
var_dump($a);

$arr=['name'=>'zhangsan','arg'=>18];
var_dump($arr);
```

> 接收数据

```
$_GET['name'];  //接收数据 git环境下
$_POST['id']; //接收数据，post环境下   更安全，不在地址显示数据

```


> 采用get发送请求
```
xml.open('get','yinru.php?id=news',true);//方式   路径   是否异步

/*发送请求*/
xml.send();    
    
```

> 采用post发送请求
```
//      xml.open('post','data.php',true);//采用post
//      xml.setRequestHeader("ContZent-Type","application/x-www-form-urlencoded");
//      xml.send('id=ty');

```
























