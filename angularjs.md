# angularjs笔记

## 一、概念
> google基于js开发的mvc框架，简化前端开发的负担，提供了一套兼容性很好并且可扩展的服务，包括数据绑定，dom操作，mvc设计模式和模块加载等

## 二、适合场景
* 单页面web应用
* （大量数具操作）crud的管理系统的开发
* 开发前后端分离的应用
* 前后端交互频繁 ，大量的ajax请求


## 三、历史 
> 虽然是比较新的技术，09年诞生,但不火了，2012  版本1.0,
 2014年秋天，2.0，,217年3月发布4.0，版本稳定性太差，但是1.0是稳定的

## 四、核心思想
* 依赖注入
* 模块化
* 双向数据绑定（mvvm）
* mvc
* 指令  对于html进行的扩展（重新定义html标签或属性）

## 五、为什么使用它？

* 前后端分离
* 减轻服务端压力：服务器只用出数据
* 同一套后端程序代码，不用修改就可以用于web页面，手机，平板等多种客户端


#### 业务逻辑
> 实现核心功能的代码就叫业务逻辑

## 六、指令
> ng 开头

### ng-app  
* ng-app 指令用于告诉 AngularJS 应用当前这个元素是根元素。
* 所有 AngularJS 应用都必须要要一个根元素。
* HTML 文档中只允许有一个 ng-app 指令，如果有多个 ng-app 指令，则只有第一个会被使用。
##### 注意：
* 指定页面中的那一部分接受他的管理;
* 页面中如果有多个，则只有一个生效，
* 放在html上则整个页面受她管理

### {{ }}
> 做数据绑定用的  模板

### ng-model
> 定义数据模型，下面的name 是数据模型，控制器是angularjs内置的
```
 <div >
        <p>名字 : <input type="text" ng-model="name"></p>
        <hr/>
        <h1>Hello {{name}}</h1>
    </div>
```

#### 注意：在input上写了ng-model，则本身的value不可用

### ng-init
> 初始化模型的值
```
ng-init="name='zhangsan'"

```
###  ng-bind 
> 给指定的标签绑定的数据
### ng-repeat 
> 遍历数组，

  * 不允许重复id,字符或者数字的时候把自身作为id
     * 解决方法track by 
     > 业务上生成自己的id
       ```
    
```
 <div ng-repeat= "(i,val)  in  arr  track by i">
    {{val}}
 </div>
```
    
  * 自身存在一些参数 
     * $index 下标 （0...length-1)
     * $first  是否为第一个 
     * $last   是否为最后一个
     * $even   是否是偶数
     * $odd    是否是奇数
     * $middle  当元素处于第一个和最后一个之间是
     
### ng-repeat-start  ng-repeat-end

```
<script>
    var myapp=angular.module('nnapp',[]);
    myapp.controller('mycontrol',function($scope){
        $scope.arr=['lisi','zhangsasan','wangwu','maliu','zhangqi','lisi'];
        $scope.name='zhanghsan';
        $scope.json=[
            {name:'zhangsan',arg:18},
            {name:'lisi',arg:20},
            {name:'lisijsfh',arg:202}


        ]
    })
</script>
    

    <ul  ng-app="nnapp">
            <li  ng-repeat-start="val in json">{{val.name}}</li>
            <li  ng-repeat-end >{{val.arg}}</li>
    </ul>

```

### 过滤器
> 将数据格式化展示，ng中
* currency 格式化数字为货币的形式

```
{{num | currency:'$':2}}

```
* filter 筛选
```
  <li ng-repeat="val in json | filter:{name:'lisi'}">{{val.name}}</li>
  <li ng-repeat="val in json | orderBy:'arg' | filter:{name:'lisi'}">{{val.arg}}</li>
```

* uppercase  转化成大写
```
 {{ name | uppercase|lowercase}}
 
```
* lowercase  转化成小写

```
 {{ name | uppercase|lowercase}}
 
```

* number  转化成数字，带有格式的
```
 {{number | number:4}}
```
* date:'medium'   转化时间 
* date:"yyyy-MM-dd hh:mm:ss a EEE w  GGGG"  将时间转化为指定格式
```
下面是angularjs内置的日期格式化
{{ now | date:'medium' }}<!-- Dec 3, 2016 10:43:51 AM -->
{{ now | date:'short' }}<!-- 12/3/16 10:43 AM -->
{{ now | date:'fullDate' }}<!-- Saturday, December 3, 2016 -->
{{ now | date:'longDate' }}<!-- December 3, 2016 -->
{{ now | date:'mediumDate' }}<!-- Dec 3, 2016 -->
{{ now | date:'shortDate' }}<!-- 12/3/16 -->
{{ now | date:'mediumTime' }}<!-- 10:43:51 AM -->
{{ now | date:'shortTime' }}<!-- 10:43 AM -->

年份格式化
四位年份： {{ now | date:'yyyy' }} <!-- 2016-->
两位年份： {{ now | date:'yy' }} <!-- 16-->
一位年份： {{ now | date:'y' }} <!-- 2016-->

月份格式化
英文月份： {{ now | date:'MMMM' }} <!-- December -->
英文月份简写： {{ now | date:'MMM' }} <!-- Dec -->
数字月份： {{ now |date:'MM' }} <!-- 12 -->
一年中的第几个月份： {{ now |date:'M' }} <!-- 12 -->

日期格式化
数字日期： {{ now | date:'dd' }} <!-- 03 -->
一个月中的第几天： {{ now | date:'d' }} <!-- 3 -->
英文星期： {{ now | date:'EEEE' }} <!-- Saturday -->
英文星期简写： {{ now | date:'EEE' }} <!-- Sat -->

小时格式化
24小时制数字小时： {{now | date:'HH'}} <!-- 10 -->
一天中的第几个小时： {{now | date:'H'}} <!-- 10 -->
12小时制数字小时： {{now | date:'hh'}} <!--10-->
上午或下午的第几个小时： {{now | date:'h'}} <!--10-->


分钟格式化
数字分钟数： {{ now | date:'mm' }} <!-- 43 -->
一个小时中的第几分钟： {{ now | date:'m' }} <!-- 43 -->

秒数格式化
数字秒数： {{ now | date:'ss' }} <!-- 51 -->
一分钟内的第几秒： {{ now | date:'s' }} <!-- 51 -->
毫秒数： {{ now | date:'.sss' }} <!-- .535 -->

字符格式化
上下午标识： {{ now | date:'a' }} <!-- AM -->
四位时区标识： {{ now | date:'Z' }} <!--- +0800 -->

{{ now | date:'MMMd, y' }} <!-- Dec3, 2016 -->
{{ now | date:'EEEE, d, M' }} <!-- Saturday, 3, 12 -->
{{ now | date:'hh:mm:ss.sss' }} <!-- 10:43:51.535 -->

```
* limitTo:2;数组、字符串
```
  <li ng-repeat="val in arr | limitTo:2">{{val}}</li>
  
```
* orderBy:'+'  排序
* orderBy:'+arg'   排序可以加变量名

```
 <li ng-repeat="val in json | filter:{name:'lisi'}">{{val.name}}</li>
          <li ng-repeat="val in json | orderBy:'arg' | filter:{name:'lisi'}">{{val.arg}}</li>
```

### 自定义过滤器
```
{{带过滤数据 | 过滤器名：参数1：参数2：参数3.....}}


app.filter('过滤器名', function () {
        return function (待过滤数据, 参数....) {
                      ......
            return  已过滤数据;
 }
 
 ```

> 可以在那些地方用
* 可以在模板
## 七、 控制器
### $scope
>  是构成整个anglularjs应用的核心基础，在整个框架中都被广泛的使用。

    $scope对象是定义应用业务逻辑、控制器方法和视图的地方。
    作用域是应用的基础状态




### $watch
> $watch是一个scope函数，用于监听模型变化，dang你的模型发生变化时会通知你。
```
$watch(watchExpression,listener,objectEquality);
```
* watchExpression:监听对象，可以是一个表达式如'name',或者函数如function(){return $scope.name }

* listener:当watchExpression变化时会被调用的函数或者表达式，他接受3个参数：newvalue(新值)，oldvale(旧值)，scope(作用域的引用)

* objectEquality：是否深度监听，如果设置为ture，他告诉angular检查所监控的对象中每一个属性的变化。如果你希望监控数组的个别元素或者对象的属性而不是一个普通的值，你就使用它。

```
 $scope.arr=[];
 
  $scope.sum=function(){
        $scope.he=0;
        angular.forEach($scope.arr, function(val,key){
             $scope.he+=val.price*val.num;

        })
    }
    
    
 $scope.$watch('arr',function(){
       $scope.sum();
   },true)
   

```
## Scope提供$watch方法监视Model的变化。
## cope提供$apply方法传播Model的变化。

## 八、Anguljs 表达式
* html当中的一个代码片段
* 全都来自$scope

### 运算
* 不可以使用自增等高边原值的
* 比较运算符可以用，但是有时有bug,需要空格

### dom属性
* 字符串的属性和方法只要不改变原数组就可以用









