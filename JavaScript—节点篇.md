---
title: JavaScript—节点篇
tags: 李松,2017.4.30
grammar_cjkRuby: true
---

## 一、获取节点

#### 以下没有兼容性问题
####  1、获取（box）父节点
console.log(box.parentNode);
#### 2、获取（box）子节点
console.log(box.childNodes);
#### 3、获取（box）第一个子节点
console.log(box.firstChild);
#### 4、获取（box）最后一个子节点
console.log(box.lastChild);
#### 5、获取（box）同级的下一个节点
console.log(box.nextSibling);
#### 6、获取（box）同级的上一个节点
console.log(box.previousSibling);

#### 7、获取（box）节点类型
console.log(box.nodeType);
#### 8、获取（box）节点名字
console.log(box.nodeName);
#### 9、获取（box）节点值
console.log(box.nodeValue);

## 二、节点类型表

|          | 节点类型 | 节点名字  | 节点值     |     
| -------- | -------- | --------- | ---------- | 
|          | nodeType | nodeName  | nodeValue  |  
| 元素节点 | 1        | 标签名    | null       |  
| 属性节点 | 2        | 属性名    | 属性值     |   
| 文本节点 | 3        | #text     | 文本       |    
| 注释节点 | 8        | #comment  | 注释的文字 |    
| 文档节点 | 9        | #document | null       |    


## 三、获取元素节点
#### 以下在ie8下有兼容性问题

#### 1、获取（box）子元素
console.log(box.children);
#### 2、获取（box）第一个子元素
console.log(box.firstElementChild);
#### 3、获取（box）最后一个子元素
console.log(box.lastElementChild);
#### 4、获取与该元素（box）同级的下一个元素
console.log(box.nextElementSibling);
#### 5、获取与该元素（box）同级的上一个元素
console.log(box.previousElementSibling);
#### 6、获取（box）子元素的个数
console.log(box.childElementCount);


## 四、增删改查

### （1）、增
#### 1、创建一个元素节点
var zi5=document.createElement("div");
```
//给元素添加一个类名
zi5.classList.add("zi5");

//移除元素类名
zi5.classList.remove("zi5");

//给元素添加一个内容
zi5.innerHTML="08";
```
#### 2、追加
```
var box2=document.getElementsByClassName("box")[0];
var zi2=document.getElementsByClassName("zi2")[0];
var zi4=document.getElementsByClassName("zi4")[0];
var zi3=document.getElementsByClassName("zi3")[0];

```

#### 方式1：父对象.appendChild(要追加的元素)

给父对象(box2)的子元素的末尾追加一个元素节点（zi5）
box2.appendChild(zi5);

#### 方式2：给(zi2)的前面追加一个元素节点

给(zi2)的前面追加一个元素节点
box2.insertBefore(zi5,zi2);

### （2）、删除
删掉（box2)的子节点（zi2) 

box2.removeChild(zi2);

### (3)、修改

将元素（zi3)换成元素（zi5)
box2.replaceChild(zi5,zi3);

