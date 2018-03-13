# 服务

$scope、$interval、$timeout、$rootScope

```
app.controller('',function($scope,$interval,$timeout,$filter))
```
$q:处理异步

## $http 

> $http是angular

    $http({
        method:'get post put delete',
        url:'',
        params:'k=v&k1=v1&k2=v2,{k:v,k1:v1}',
        data:'k=v&k1=v1&k2=v2,{k:v,k1:v1}'
    })
$http 返回的是延迟对象


前后台分离

后台：test  http://localhost:3000
后台：8080   http://localhost:8080


## promise 解决回调函数的问题

```
一种模式，以同步的方式执行异步的函数
```
* 两件事情：1.指定承诺所需完成的事


> $q是angularJ中自己封装的


## $localtion 
地址栏（操作url）
http://www.baidu.com:8080/user/user.
php#hash?user=guset&v=123


$localhost 封装了JS上localhost上的方法属性


$q   $http  $location

* $location.absUrl()      URL
* $location.protocol() 协议
* $location.host()     主机名
* $location.port()      端口号
* $location.url()        获取和设置哈希
* $location.search() 返回和设置URL查询字符串内容
* $location.path()   返回和设置当前路径        在angular  路径的变化就是哈希的变化


### 自定义服务
> 服务作用就是对外提供某个特定的功能，如信息服务，文件压缩服务等，是一个独立的模块

> 服务的主要功能：存储数据  提供功能

> ng的服务是这样的定义的：
- 它是一个单例对象或者函数，对外提供特定的功能；
- 服务是一个单例（在每个应用中只会实例化一次）
- 服务能够提供在应用生命周期内保持数据的方法，（依赖注入）并保持数据一致。

> 常用的服务有如下几个；
- $scope
- $rootScope
- timeout()

### 创建服务
> factory()  对象

> provider 返回函数




