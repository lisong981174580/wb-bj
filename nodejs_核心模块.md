# nodejs核心模块
## fs模块
### 错误信息处理方式
* throw
```
if(error)throw error;
```
* console.error();
* try catch  
```
try{
    
}catch{
    
}
```

## 创建文件夹时需要注意两点
* 1、在指定目录创建子文件夹时，父级目录必须存在，否则会报错
* 2、不能重复创建
 

## 查看文件夹状态
* fs.stat(path,callback)  异步查看文件或文件夹状态  callback(err,stats)
* fs.statSync(path)   同步查看文件夹或文件夹的状态，path返回一个fs.stats的实例
 

## Nodejs事件模块EventEmitter
### events使用方式
* 构造函数继承
* es6使用类继承
* 直接使用

## http模块
* http 超文本传输协议
* 服务器
* 客户机

## 本质区别
* get 得
* post 发

## 搭建http服务器软件
* apache
* iis
* Nginx

> nodejs 提供了http这个模块，自己开发http

## 小练习
* 将服务器的时间发给客户端


## 响应头
* setHeader
* statudCode

## ajax上传文件

* 1.inputDOM上的一个属性files               保存上传文件的列表,我们上传的都在files[0](如果只有一个上传input) files->file
* 2.FormData 对象，可以把form中所有表单元素的name与value组成一个queryString，提交到    后台。在使用Ajax提交时，使用FormData对象可以减少拼接queryString的工作量。

* 3、FormData 对象上有一个append方法，可以保存数据，这样就可以发到后台了。
* 4、处理图片需要用到一个包formidable


##  http.requrest()  客户端
