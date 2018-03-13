# reactjs
> 案例参考地址  https://git.coding.net/lisong181650/weather.git
## 一、 前端发展史
* 1.静态页面
* 2.php 、jsp、动态页面面、后台
* 3.后台 mvc
* 4.ajax 出现  spa
* 5.前台 mvc
* angular.js 、 ember.js 、 backbone.js
* 6.组件化开发 单项数据流
* 7.angular.js
* 8.react.js

## 二、react.js概念

> 是一个开发用户的js库

> 核心理念就是组件

> 用户界面是通过一个个组件拼合而成

> 组件的作用：提高开发效率、便于维护改进


## react虚拟dom
###  优点：
* 提高性能（dom操作man  通过dff算法）
* 通过虚拟dom抽象  可以在其他终端上使用复用（跨平台）

### angularjs  backbonejs  emberjs 
> 在html中写js代码  {{ js }}   v-repeat

### react
> 在js中写html代码

## react使用
* react.js核心库
* react-dom.js 将组件渲染成dom
* babel.js 将jsx语法==> js 语法   编译库


## 核心方法
* js提供的对象  React、ReactDOM

## 创建虚拟dom
* React.createElement(标签名| 组件，属性，内容)

### 渲染
ReactDOM.render(
    html tag | 虚拟dom | 组件，要渲染的内容

)

## 格式
```
### 组建类
ES5

var 组建类名=React.createClass({
    render:function(){
        return (组件结构)
    }
})
var 虚拟DOM=React.createElement(组件类名)

ES6

class 组建类名 extends React.Component{
    render(){
        return (组件结构)
    }
}
var 虚拟DOM=React.createElement(组件类名)

### 函数式组件
function 组件类名(props){
    return (组件结构)
}
var 虚拟DOM=React.createElement(组件类名)

# jsx   JavaScript XML
jsx=html标签+自定义标签(组件)

```
## 案例

#### 案例一:
```
 
 /*创建一个虚拟dom
     React.createElement('组件|标签',属性(前两个参数必须填),内容)
    */
	var  div=React.createElement('div',{'title':'red',id:'ceshi'},'这是div');
	/*获取一个dom元素*/
    var  box=document.querySelector('#box')
    /*将虚拟标签渲染到指定元素下，后面接受一个回调函数*/
	ReactDOM.render(div,box,function(){
		console.log('渲染成功')
	})
```

#### 案例二：
```

    /*获取dom元素*/
	var  box2=document.querySelector('#box2')
	/*创建一个组件*/
    var  h3=React.createClass({
		render:function(){
			return(
				React.createElement('h3',null,'这是测试')
			)
		}
	})


    /*把组件作为参数传给vuni对象*/
    var h=React.createElement(h3,null,'')

    /*把该用组件创建的虚拟对象渲染到页面中*/
	ReactDOM.render(h,box2);
```

#### 案例三：

```

	class Hello extends React.Component {
	  render() {
	     return React.createElement('h3',null,'世界你好')
	  }
	}


	 var he=React.createElement(Hello,null,'')
	ReactDOM.render(he, document.querySelector('.box3'));

```

### babeljs使用方法
#### (1)、引入核心库 和dom库
```
<script src="https://cdn.bootcss.com/react/15.4.2/react.min.js"></script>
<script src="https://cdn.bootcss.com/react/15.4.2/react-dom.min.js"></script>
<script src="https://cdn.bootcss.com/babel-standalone/6.22.1/babel.min.js"></script>

```

#### (2)、修改script标签type类型
```
type='type/babel'
```

#### (3)、规则
* 组件  首字母大写
* 标签  首字母小写
* {}    写变量
* 驼峰命名规则

#### (4)、特殊标签htmlFor、className
```
<label    for=''> </label>
写成
<label    htmlFor=''> </label>
```
## jsx 简介
* jsx =html标签 + 自定义标签（组件）

## 写jsx 注意问题

* 1.创建组件类  名称首字母必须大写
* 2.包的标签只能有一个
* 3.标签可以为单标签或双标签、单标签必须有结束


## jsx注释

 * 标签外 {/* */}    块级注释

 * 标签行内  //   单行注释   专门给标签假的

## 添加样式
* 方法1：类名绑定  id绑定
* 方法2：通过json格式定义style,再以变量的形放到标签中

## 获取渲染组件上的属性如name值
```

 <script type="text/babel">
          class Ref  extends React.Component{
            constructor(){
              super(arguments);
              this.state={
                    val:''
                  }
              }

           changeinput(){
               this.setState({val:this.refs.text.value})
           }

             render(){
               return(
                  <div>
                    <input type="text"  ref='text' onInput={ this.changeinput.bind(this) }  ></input>
                    <p>{this.state.val}</p>
                  </div>

                )
             }
          }
          ReactDOM.render(
            <Ref name='李四'></ Ref>,//这里name是可以通过this.props.name 获取的
            document.getElementById('box3'))
            </script>
```
### 绑定this时常用方法

#### aa.bind(obj)
* 返回一个函数
* 将aa上的this替换成obj上的this
#### call 与 apply 直接调用
* call: 参数     一个一个传
* apply:参数       传输组   
#### 区别：
> bind 返回一个新函数,call 与 apply 直接调用

### dangerouslySetlnnerHTML

```
var a={
    __html:'<a  href=""> </a>'
 }

<div dangerouslySetlnnerHTML=a></div>

```

### state 保存状态
```
this.state={
        
        val:''
                  
         }
``` 

### 设置状态
```
this.setState({val:this.refs.text.value})

```

### ref='text'  父组件引用子组件

### 类继承是一定要在构造函数上加super() ,否则没有this
```
   constructor(){
              super(arguments);
              this.state={
                    val:''
                  }
              }

```

### 列表加key(很重要，提高性能)

### 提高性能的方法
* key值唯一，推荐用id

### 开发时用jxs开发 
* jsx ==> js  上线后不需要引用babel

### 使用banba步骤
> babel  jsx ==>js

## 1. 全局安装 babel-cli
npm install -g babel-cli
## 2. 将es6(ecma2015)==>es5
npm install babel-preset-es2015
## 3.在根目录创建 .babelrc文件
> 文件中内容为
```
{
    "presets":['es2015','react']
}

```
## 或者也可以使用命令行
```

echo {"presets":["es2015","react"]} > .babelrc

```
## 下载react
> jsx==>js
```
npm install babel-preset-react

```
## 编译:操作步骤

- 手动编译指定文件
```
babel index.jsx --out-file index.js
```
- 监测文件变化 自动编译
```
babel index.jsx --out-file index.js --watch
babel index.jsx -o index.js -w
```
- 手动编译
```
babel jsx --out-dir js
```
- 检测文件夹中文件变化，实现自动编译
```
babel jsx --out-dir js --watch
babel jsx -d js -w
```

