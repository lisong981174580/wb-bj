## angular-指令
### 一、指令的类型
1. 属性指令 A
2. 类指令 C
3. 元素指令 E
4. 注释指令 M

### 二、自定义指令
#### 结构

```
app.directive('指令名称 ',function(){
	return {

		restrict:'EA', //指令类型
		template:'html模板' , //内容    接受字符串或者函数
		replace:true | false, //是否替换所有占位符   默认false

		<!-- 用它就不用 template-->
		templateUrl:'外部html文件（ajax）'//本地运行需要服务器

		scope:false | true | {}

		   <!-- false --> 
			false：继承父级作用域  默认参数

			<!-- true -->
			true: 表示继承父级作用域并创建了自己的作用域

			<!-- {} --> 

			{
          
                {name:'@'}: 将属性值穿过来，单向的
				{name:'='}: 将属性值作为变量传过来，双向的
				{name:'&'}: 直接把函数穿过来

			}:表示自身是一个隔离的作用域
			
		controller:""  |  function($scope){}

        transclude:flase | true  
       <!--  如果不想让指令内部的内容被模板替换，可以设置这个值为true。一般情况下需要和ngTransclude指令一起使用。  -->


        <!-- 链接函数负责注册DOM事件和更新DOM。它是在模板被克隆之后执行的，它也是大部分指令逻辑代码编写的地方。 -->
        
        link:function(scope,element,attrs){
           		操作DOM
           }



    }
})

```
### 案例：

```
var app=angular.module('myapp',[]);
    app.controller('control',function($scope){

        $scope.data=[
            {name:'李松',arg:24},
            {name:'李四',arg:25},
            {name:'王五',arg:25},
            {name:'马六',arg:24},
            {name:'整齐',arg:28}
        ]

    })

//定义指令
app.directive('hello ',function(){
	return {
		restrict:'EA', //指令类型
		template:'<div>\    或者  templateUrl:'./out.html'  //外部引入
		<p>hello word <p>\
		</div>' , //内容
		replace:true //替换所有占位符
    }
})

//使用指令

// 注释标签引用方法
<!-- directive:hellow expression -->

//一般用法
<hello></hello> 

//带上数组
<hello ng-repeat="val in data" ></hello>

```


