---
title: php
tags: 李松,2017.6.23
grammar_cjkRuby: true
---

# php

## 软件架构
## 通讯
* IP
* DNS
* http  tcp/ip  (七层）  三次握手七次挥手
* 头信息：请求头（告诉他我去哪访问），响应头
* 网站访问的过程
* 媒体类型

## php环境
* 集成开发环境  
> wamp=window  apache(用来解析php，里面有php模版，提供服务）  mysql php
* 配置

## php是什么
> 超文本预处理器，开源的，运行在服务器的脚本语言
## php文件 
>PHP 文件可包含文本、HTML、JavaScript代码和 PHP 代码
 PHP 代码在服务器上执行，结果以纯 HTML 形式返回给浏览器
 PHP 文件的默认文件扩展名是 ".php"
## 干什么
> 操作数据库
## 为什么用php

>PHP 可在不同的平台上运行（Windows、Linux、Unix、Mac OS X 等）
 PHP 与目前几乎所有的正在被使用的服务器相兼容（Apache、IIS 等）
 PHP 提供了广泛的数据库支持
 PHP 是免费的，可从官方的 PHP 资源下载它： www.php.net
 PHP 易于学习，并可高效地运行在服务器端
 
 
 ## 变量
 * 双引号里识别变量，所以一般写字符串用单引号，比较高效
 * 变量在字符串里 可以是 ｛$a} 或者  ${a}
 *  字符串的拼接用  .

## 数组
* 索引数组
* 关联数组


## 数据类型
* 标量
> int boolean string float
* 复合型
> arry object
* 特殊
> null resource
## 获取数据类型  gettype(var)
## 数据类型的转换
> (int) var
* 通过函数来设置数据类型
> settype(var,type)

## 检测数据类型
* is_init()   is_integer()
* is_string()
* is_float()


## 检测变量是否设置  isset(var)
## 检测变量是否为空  empty(var)  
> 如果变量存在且不为0、‘’、‘0’、false、null、空数组、空对象，则为false

## 判断是否真的是空的
inset(var) && empty()


## 销毁变量 unset(var)

## 作用域
* 全局作用域
* 局部作用域
* 静态不做用域 static
* 
## 超全局标量

* $GLOBALS   获取全局变量
* $_GET  获取所有通过git发送过来的数据
* $_POST
* $_REQUEST   可以获取所有变量
* $_COOKIE  保存在浏览器上的数据
* $_SESSION 保存在服务器上的
* $_SERIVER


## 魔术变量
* _LINE_   获取行数
* _DIR_    获取目录

## 可变变量
> 变量的名称由另一个变量决定
```
$a='b';
$b='c';

//以下为可变量
$$a;
```
## 常量
>常量创建  define('NAME',value,[true]);
* 大小写敏感，在定义时可以设置
* 默认情况下时全局作用域
* 不能重复定义
* 创建时不能用$ 修饰，只能是指定的数据类型，并且是标量
* 名字默认用大写

## 长度

* 数组的长度 count(数组名）
* 字符串的长度en(字符串名）


## 系统
### 前台
### 后台
  * 入口
  * 登录、注册
  * 后台主页面
    * 用户
    * 栏目的管理
      * 对（顶层、二级）栏目进行增删改查
    * 文章管理
      * 在制定栏目下对文章增删改查
    * 设置基本信息
  * 退出
  
  ### 数据库
  
  * user
    * uid      uname   upass
      tinint       
      主键
      自增
  * category
  * article
  * site
  
  
  
  
  ## 文件结构
  
  * admin  后台逻辑
  * index  前台逻辑
  * libs   公共的函数
  * static  静态资源  css  js   images  fonts
  * template   模版
      * admin  后台模版
      * index  前台模版
  * upload   上传文件
  
  * admin.php   后台入口文件
  * index.php   前台入口文件
