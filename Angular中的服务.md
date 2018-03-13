# Angular中的服务

在Angular中，服务的本质是一些和控制器捆绑在一起的可替换的对象，通过这些对象提供了在应用的整个生命周期都存有数据的方法，当重载或刷新页面时，数据不会被清除，而且还与加载之前保持一致。

## Angular服务介绍

在Angular中服务是一种单例对象。服务主要的功能是为实现应用的功能提供数据和对象。它又可以分为内置服务和自定义服务

## 内置服务

### Angular提供了很多内置服务，如$scope、$http、$window、$location等。

    html：

    <div ng-controller="MyController">
      <div>当前的地址是： {{url}}</div>
      <button ng-click="onclick()">显示地址</button>
    </div>
    var myapp = angular.module('MyApp', []);
    myapp.controller('MyController', ['$scope', function($scope){
      $scope.onclick = function () {
        $scope.url = $location.absUrl();
      }
    }])
$location服务除了包含absUrl()方法外，还有search()和path()等方法。同时它还提供了$locationChangeStart和$locationChangeSuccess方法

### 自定义服务

自定义服务有两种方法，一是使用内置的$provider服务，另一种是调用模块(Module)中的服务注册方法，如factory、service、constant和value等方法

    html:
    
    <div ng-controller="myCtrl">
      <div>服务返回的值：
        <span>{{info('name')}}</span>
        <span>{{info('sex')}}</span>
        <span>{{info('score')}}</span>
      </div>
    </div>
    javascript:
    
    var app = angular.module('myApp', []);
      app.factory('$output', function () {
        var stu = {
          name: '张三',
          sex: '男',
          score: 60
        }
        return stu;
      });
      app.controller('myCtrl', ['$scope', '$output', function ($scope, $output) {
        $scope.info = function (n) {
          for (_n in $output) {
            if (_n == n) {
              return ($output[_n]);
            }
          }
        }
      }]);
### 创建Angular服务

在Angular中创建自定义服务，只需要先构建一个模块(Module)，然后在构建过程中调用内置的$provide服务，通过该服务的工厂函数来创建属于自己的Angular服务。除此之外，还可以调用模块中的factory、service、constant、value方法来创建。

自定义服务

服务作用就是对外提供某个特定的功能，是一个独立模块

服务的主要功能为了实现应用的功能提供数据和对象

在Angular中，服务的本质是一些和控制器捆绑在一起的可替换的对象，通过这些对象提供了在应用的整个生命周期都存有数据的方法，当重载或刷新页面时，数据不会被清除，而且还与加载之前保持一致。

### angular服务的定义
服务是一个对象 函数
在每个应用实例化一次
提供在应用生命周期内保持数据的方法，并保持数据的一致
### 自定义服务
自定义服务有两种方法，一是使用内置的$provider服务，另一种是调用模块(Module)中的服务注册方法，如factory、service、constant和value等方法

### $factory方式创建的服务，作用就是返回一个有属性有方法的对象
    app.factory('myFactory', function() {
    var service = {};//定义一个Object对象'
    service.name = "张三";
    var age;//定义一个私有化的变量
    //对私有属性写getter和setter方法
    service.setAge = function(newAge){
    age = newAge;
    }
    service.getAge = function(){
    return age;
    }
    return service;//返回这个Object对象
    });
### service服务
通过service方式创建自定义服务，相当于new的一个对象：var s = new myService();，只要把属性和方法添加到this上才可以在controller里调用。
    app.service('myService', function($http,$q) {
    this.name = "service";
    this.myFunc = function (x) {
    return x.toString(16);//转16进制
    }

### $provider所有的服务都是由$provider服务来创建的
只有provder是能传 .config() 函数的 service。如果想在 service 对象启用之前，先进行模块范围的配置，那就应该选择 provider。需要注意的是：在config函数里注入provider时，名字应该是：providerName+Provider.
使用Provider的优点就是，你可以在Provider对象传递到应用程序的其他部分之前在app.config函数中对其进行修改。
当你使用Provider创建一个service时，唯一的可以在你的控制器中访问的属性和方法是通过$get()函数返回内容。

    var app = angular.module('myApp', []);

    //需要注意的是：在注入provider时，名字应该是：providerName+Provider   
    app.config(function(myProviderProvider){
        myProviderProvider.setName("大圣");
    });
    app.provider('myProvider', function() {
        var name="";
        var test={"a":1,"b":2};
        //注意的是，setter方法必须是(set+变量首字母大写)格式
        this.setName = function(newName){
            name = newName
        }

        this.$get =function($http,$q){
            return {
                getData : function(){
                    var d = $q.defer();
                    $http.get("url")//读取数据的函数。
                        .success(function(response) {
                            d.resolve(response);
                        })
                        .error(function(){
                            d.reject("error");
                        });
                    return d.promise;
                },
                "lastName":name,
                "test":test
            }
        }

    });
    app.controller('myCtrl', function($scope,myProvider) {
        alert(myProvider.lastName);
        alert(myProvider.test.a)
        myProvider.getData().then(function(data){
            //alert(data)
        },function(data){
            //alert(data)
        });
    });

    使用constant和value方法自定义服务
    
    使用constant和value方法创建服务，常用于返回一个常量。
    
    app.constant(name, value)
    app.value(name, value)
    html:
    
    <div ng-controller="MyController">
      <div class="show">图书ISBN号: {{BOOK}}</div>
      <div class="show">美元兑换价: {{USD}}</div>
    </div>
    javascript:
    
    var myapp = angular.module('MyApp', []);
    myapp.constant('$ISBN', {
        BOOK: '9898733238'
    });
    myapp.value('$RATE', {
        USD: 614.28
    });
    myapp.controller('MyController', function($scope, $ISBN, $RATE){
        var n = 600;
        angular.extend($RATE, {USD: n});
        $scope.BOOK = $ISBN.BOOK;
        $scope.USD = $RATE.USD;
    })
管理服务的依赖

添加自定义服务依赖项方法

我们在自定义服务时，会添加其他各类对象或服务，有下面三种方式：

(1) 隐式声明

在参数中直接调用，但这种方式在代码压缩时注入的对象可能会失效

app.factory('ServiceName', function(dep1, dep2) {})
(2) 调用$inject属性

将需要注入的服务对象包装成一个数组，作为$inject的属性值，但这种方式效率很低

var sf = function(dep1, dep2) {};
sf.$inject = ['dep1', 'dep2'];
app.factory('ServieceName', sf);
(3) 显式声明

在创建服务的函数中，添加一个数组，在数组中按顺序声明需要注入的服务或对象名称，这种方式既高效也不会丢失代码，推荐使用

    app.factory('ServiceName', ['dep1', 'dep2', function(dep1, dep2) {} ])
    html:
    
    <div ng-controller="MyController">
      <div class="show">你选择的是:{{result}}</div>
      <button ng-click="confirm('你真的要删除这条记录吗?')">删除</button>
    </div>
    javascript:
    
    var myapp = angular.module('MyApp', []);
    
    myapp.service('notify', ['$window', function ($win) {
      return function (msg) {
        return $win.confirm(msg) ? '确定' : '取消';
      }
    }]);
    
    myapp.controller('MyController', ['$scope', 'notify', function ($scope, notify) {
      $scope.confirm = function (msg) {
        $scope.result = notify(msg);
      }
    }]);
嵌套注入服务

在Angular中，有时需要将一个自定义的服务注入到另一个自定义的服务中，形成嵌套注入的形式，通常只需要将被注入的服务作为内置服务，采用显式声明的方式注入即可

    html:
    
    <div ng-controller="MyController">
      <button ng-click="ask(false, '你输入的内容不正确')">提示框</button>
      <button ng-click="ask(true, '你真的要删除这条记录吗?')">询问框</button>
    </div>
    javascript:
    
    var myapp = angular.module('MyApp', []);
      // 使用factory定义confirm服务
      myapp.factory('confirm', ['$window', function ($win) {
        return function (msg) {
          $win.confirm(msg);
        }
      }]);
      // 将confirm服务显式的注入到notify服务中
      myapp.service('notify', ['$window', 'confirm', function ($win, con) {
        return function (t, msg) {
          return (t) ? con(msg) : $win.alert(msg);
        }
      }]);
      myapp.controller('MyController', ['$scope', 'notify', function ($scope, notify) {
        $scope.ask = function (t, msg) {
          notify(t, msg);
        }
      }])
添加服务的其他设置

创建好的服务一般比较复杂，如果后期需要修改，往往面临很高的风险，Angular为服务添加了一些设置项，如装饰器(decorator)，可以在不修改原代码的情况下为服务添加其他功能

服务的装饰器

装饰器(decorator)是Angular中内置服务$provide所特有的一项设置函数，通过它可以拦截服务在实例化时创建的一些功能，并对原有功能进行优化和替代。

$provide.decorator('ServiceName', Fn)
$provide表示注入后创建的服务对象
ServiceName表示需要拦截的服务名称
Fn表示服务在实例化时调用的函数，该函数在执行时需要添加一个名为$delegate的参数,该参数代表服务实例化后的对象，服务的新功能就是通过这个对象进行扩展和优化的
示例代码：

    <div ng-controller="MyController">
      <div class="show">姓名: {{stu.name}}</div>
      <div class="show">邮件: {{stu.email}}</div>
      <div class="show">主题: {{stu.title}}</div>
    </div>
    var myapp = angular.module('MyApp', []);
      // 使用工厂函数factory定义student服务
      myapp.factory('student', function () {
        return {
          name: 'Kaindy',
          email: 'kaindy7633@gmail.com'
        }
      });
      // 使用$provider的装饰器decorator为服务student扩展一个title属性
      myapp.config(function ($provide) {
        $provide.decorator('student', function ($delegate) {
          $delegate.title = 'Hello, Angular!';
          return $delegate;
        })
      });
    
      myapp.controller('MyController', function ($scope, student) {
        $scope.stu = student;
      });
