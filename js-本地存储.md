---
title: js-本地存储 
tags: 李松,2017.5.15
grammar_cjkRuby: true
---

## 一、coke  适用于火狐
#### 特点：
1、存储计算机中的一个字符串，用于存储数据，大小4k，可以使用js进行获取和设置。
2、记录在硬盘中，记录密码，当再次打开的时候可以反馈给你。
3、用途:记住密码...
4、设置：临时  有时间的（国际标准时间）
5、不同的浏览器创建的是不同的cookie   因为不同的浏览器在计算机中的内存是不一样的
6、不能跨域  域名 （现在测试都是在本地上测试的）
例子：笔记模版/coke

## 二、localStorage 火狐谷歌都可以用
#### （1）、 localStorage	//内存大小为5-10M;  一直保存     也不能跨域
#### （2）、 sessionStorage;  // 周期为 关闭就消失    关闭掉浏览器就消失
### 1、设置
#### 三种方式
	localStorage.aa="bb";
	localStorage["cc"]="dd";
	localStorage.setItem("ee","ff");
### 2、获取
#### 三种方式
	localStorage.cc;  //在另一张页面也可以获取到
	console.log(localStorage.cc);
	
	localStorage["cc"];
	console.log(localStorage["cc"]);
	
	localStorage.getItem("ee");
	console.log(localStorage.getItem("ee"));
	
### 2、删除
#### 三种方式

	localStorage.removeItem("aa");
	localStorage.clear();//清空所有

### 注意：由于只能保存为字符串形式，故保存时需要转换为字符串，获取时再转换为json格式	

	var date1={x:1,y:2,z:3};
	console.log(date1);
	date1=JSON.stringify(date1);//json转为字符串格式，因为localStorage里面只能存字符串
	console.log(date1);
	localStorage.Date1=date1;
	
	var jsonData=JSON.parse(localStorage.Date1);//转化为json格式
	console.log(jsonData);
  
 