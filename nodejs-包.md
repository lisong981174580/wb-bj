# 包
为了便于管理和使用，多个模块组合而成的大模块叫做包

## 自定义包
* 按路径引入
  require('./calc/main')
* 通过默认入口require('calc') 
  1. calc 移入 node_modules
  注意：主模块必须是index.js

* 通过添加配置文件 入口require('calc')
    1. calc 移入 node_modules
    2. calc 添加 package.json
    package.json参数如下
        name 包名
        main 包入口模块路径

## Package.json 属性说明
name - 包名。
version - 包的版本号。
description - 包的描述。
homepage - 包的官网 url 。
author - 包的作者姓名。
contributors - 包的其他贡献者姓名。
dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。
repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。
main - main 字段是一个模块ID，它是一个指向你程序的主要项目。就是说，如果你包的名字叫 express，然后用户安装它，然后require("express")。
keywords - 关键字

## 符合CommonJs规范包
包是将某个独立的功能封装起来，用于发布、更新、依赖管理和版本控制

符合CommonJs规范包：
- package.json 放在根目录下
- bin 存放二进制 
- JavaScript 代码lib
- test 单元测试 
- doc 文档
- README.md 包的说明文档

## npm    (node package manager)
npm主要用于Node.js包的发布、安装、传播、依赖控制。

npmjs.com

安装一个包
```
npm install <包名称>
npm i less
npm i express
npm i express@4.5.2


npm install <包名称> --save //安装的同时创建一个包配置文件  上线用的
npm install <包名称> --save-dev  //安装的同时创建一个包配置文件  开发用的
```

## 上传步骤
```
npm init   //生成包配置文件
npm adduser    //输入npm上的账号密码
npm publish .   //上传到npm上，发布指定包
npm unpublish <包名> @版本号     //删除一个包的一个版本

```

列出所有包
```
npm ls //列出当前所有安装的包

```

卸载

```
npm uninstall <包名> --save //卸载一个包 

```
更新

```
npm updata express //更新一个包

```
搜索

```
npm search express //搜索模块
```

## 上传
```
npm publish  calc

```
## 删除
```
npm unpublish  calc@1.0.1@

```



## nodejs全局对象
## console模块
* console.log()  输出结果
* console.info() 输出相关信息
* console.error() 输出错误消息
* console.warn() 输出警告消息
* console.dir(object)  利用util.inspect（)输出对象的分析
* console.time()  在程序执行前调用、记录当前的时间信息
* console.timeEnd()   配合console.time,在程序执行完成后调用，记录程序完成后的时间信息（既间隔的时间）
* console.trace()    追踪情况
* console.assert(expr,msg)  判断某个表达或变量是否为真，如果 expr为假，则输出msg


## process模块
#### 方法
* process.cwd()  查看当前进程的工作目录
* process.chdir()  更改当前进程的工作目录
* process.stdin() 标准的输入流
* process.stdout() 标准的输出流
* process.emit()  主动触发自定义事件
* process.pause() 进程暂停
* process.resume()  进程重启
* process.memoryUsage()  内存使用情况 heap Total代表已申请到的堆内存，heapUsed当前使用的内存，rss（resident set size)进程的常驻内存（单位字节byte) 
* process.nextTick(callback)  一旦事件结束，调用回调函数
* process.uptime() 返回node已经运行的秒数
* 
#### 属性
* process.argv 是用来获取或查看当前进程的相关信息
* process.platform  运行程序所在的平台系统    darwin 、freebsd、linux、sunos或win32
* process.varsion node的版本
* process.versions 包含了node的版本和依赖


## 注意：
> 在nodejs中，所有带有回调函数的方法都是异步，代码执行时候的顺序，所有同步函数执行完成后才能执行异步

## 几个重要的异步方法
* process.nextTick（function(){})  效率高(将任务列表放到任务末尾执行）  稍微快点
* setTimeout(function(){},0)   效率低 因为要判断时间 (将任务列表放到任务末尾执行）
* setImmediate() 放到下一次事件循环执行  效率高，直接执行无判断

##魔术常量
* _filename  获得当前文件的路径  绝对路径
* —dirname   获得的当前文件的目录



## Buffer
>内存缓冲区，长度固定
#### 创建方法
* Buffer.from(array)
* Buffer.from(string[,encoding])
* Buffer.alloc(size[,val[,encoding]])

## 字符串转Buffer
Buffer.from(string[,encoding])

## Buffer转字符串
but.toString([encoding],[start],[end])

## 拼接Buffer
Buffer.concat(list[,totallength])


## Buffer判断不支持的编码类型
![enter description here][1]


  [1]: ./images/QQ%E5%9B%BE%E7%89%8720170715202330.png "QQ图片20170715202330.png"