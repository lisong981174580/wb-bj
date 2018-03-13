---
title: Node.js 
tags: 李松,2017.7.13
grammar_cjkRuby: true
---

### 一、百度开放云
> https://cloud.com
* 百度开放云实名认证（三个工作日内）  下周一

### 二、Nodejs
## 什么是nodejs?
> 是一个让JavaScript运行在浏览器之外的平台。他实现了诸如文件系统、模块、包、操作系统API、网络通讯等Core javascript 没有或者不完善的功能。
> nodejs让JavaScript可以运行在服务器端

## js在不同环境中操作的权限
* javascript是一门脚本语言（直译）
* 在浏览器的javascript中 
  * 操作DOM、BOM
* 在服务器端的javascript中 
  * 操作I\O  输入输出
  * 文件系统
  * 对系统进行操作
  * 对网络进行操作
  * 提供服务
* web服务器：一台电脑上安装了一个可以提供http服务的软件（apache、IIS、nigx)

## nodejs的优势

* 基于事件驱动、异步I\O
* 运行速度快，依赖V8引擎
* 非阻塞
* 单进程、单线程
> 进程和线程是操作系统的基本概念，cpu承担计算，cpu好比一个工厂，进程好比车间，表示cpu可以运行任务单个任务，进程一般只会运行一个，其他处于非运行状态，线程好比工人协同完成一个任务
  * 进程：车间 一条线任务
  * 线程：工人

## nodejs的劣势
* 1、不适合cpu密集型应用
    * 解决方案：分解大型运算任务为多小任务，使得运算能适时释放，不阻赛I/O的发起
* 2、只支持单核cpu，不能充分利用cpu
* 3、可靠性底
  原因：单进程、单线程
  解决方案：
  1.Nnigx反向代理
  2.开多个进程监听同一个端口，使用cluster模块
* 4、开源组件库质量层次不齐，更新快向下不兼容



## nodeJs要了解什么

静态文件处理

自动化任务管理器：grunt、 glup;
模块化打包工具：webpack、browserify;
包管理器：npm

web框架

传统框架：express、koa;
接口(API)：restify

模板引擎

将数据与视图进行结合;
ejs
jade

数据库

mongodb、mysql


## 关于多版本管理
nvmw
n


### commonjs网站 
> www.commonjs.org
> nodejs.org

### commonjs
>CommonJs规范的出现，是为了统一JavaScript在浏览器之外运行的一些规范
CommonJs规范：模块、包、系统、二进制、控制台、编码、文件系统、套接字、单元测试等
NodeJs是CommonJs规范最热门的一个实现 


## nodejs运行方式
* 1、运行方式
   * 1、命令行运行   node，写js代码  按下回车键
   * 2、node 要执行文件的路径
   * 3、在文件夹中shift键+右键


### nodejs模块系统
#### 概述：
> 在nodejs中，模块就是一个js文件，js文件可能是一个js代码，json、c/c++编译过文件。

> 在当前模块下定义的变量、函数值作用当前模块，如果作用在全局范围需要通过globao定义。

> 现在web开发变得越来越复杂，我们不得不借助软件工程中的一些方案来解决我们遇到的问题，模块化开发是我们迫切的需求
### 模块化开发主要解决的问题
    * 1、命名冲突问题
        * 解决办法：命名前加前缀  css、js都可以这么用
    * 2、文件间的依赖问题
    * 3、前端模块化
         * AMD 、 CMD
         * sea.js 、 require.js

### 加载一个模块  使用require()方法
> 原生模块：自带的,
 * 加载原生模块只需要写模块名称
    ```
    //加载原生模块
    var fs=require('fs');
    
    ```
> 文件模块：用户写的
 * 文件模块调用时必须指明路径  （'./ceshi.parse')
   * 1、 .js  通过调用js引擎编译
   * 2、 .json  通过后缀 调用JSON.parse
   * 3、 .node  c/c++ 编写
    
    
## 模块操作
> 在编写每个模块时，都有require、exports、module,三个预先定义好的变量可以使用
* 使用模块 require
    * 接受如下参数
        - http、fs 、path等，原生模块   不需要安装
        ```
        require('fs');
        ```
        - 相对路径的文件模块
        ```
        require('./ceshi.parse')
        ```
        - 绝对路径文件模块
        ```
        require('C:\Users\Administrator\Desktop\nodejs')
        ```
        - 非原生模块的文件模块
        
        ```
         require('sum')
        ```
* 定义模块\创建模块 exports、module
    * exports 的只能导出一个对象
    * module.exports  任导出的类型是可变的

### 模块初始化与优先级问题
> 模块初始化只会初始化一次    
> 模块加载优先级：已经缓存的模块>原生模块>文件模块>从文件加载



### 模块
* 内置模块
* node_modules 目录
* 主模块



### 模版引擎
    * 将数据和视图进行结合
    * ejs
    * jade
- 数据库
    * mongodb、mysql

![enter description here][1]

![enter description here][2]


  [1]: ./images/QQ%E5%9B%BE%E7%89%8720170715202608.png "QQ图片20170715202608.png"
  [2]: ./images/QQ%E5%9B%BE%E7%89%8720170715202619.png "QQ图片20170715202619.png"