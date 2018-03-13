#### 一、less简介
> css预处理器，使css写的更少，表达的更多，1以函数式思维去写css
#### 二、工具Koala编译
> 国产软件 http://koala-app.com/index-zh.html
#### 三、语法
##### (1)、注释
> 以下方式不会被编译
```
//这是编译内容

```
> 以下方式会被编译

```
/* 这是编译内容 */

```

##### (2)、变量
>  使用@+变量名
```
@a:12px

.box{
	width:@a
}

```
##### （3）、混合
> 增加css的复用性,解决兼容性很有用
```
.box{
	width:100px;
	height:200px;
}

.boder{
	 color:red;
	 .box;
}

//可带参数 可带默认值
.border(@border_width:10px){
	border:solid yellow  @border_width;
}
.test_hunhe{
	.border_02(30px);
}
```

##### （4）、匹配模式
> 相当于switch选择语句
```
.mixin (dark, @color) {
  color: darken(@color, 10%);
}
.mixin (light, @color) {
  color: lighten(@color, 10%);
}
.mixin (@_, @color) {
  display: block;
}


@switch: light;

.class {
  .mixin(@switch, #888);
}

```

##### (5)、嵌套规则
> LESS 可以让我们以嵌套的方式编写层叠样式
```
ul{
	width: 100px;
	height: 200px;
	li{
		width: 100px;
		height: 100px;
		list-style: none;
	}
	a{
		text-align: center;
		padding: 5px;
		text-decoration: underline;
		&:hover{
			color:red
		}
	}
}
```
##### (6)、@arguments变量
> @arguments包含了所有传递进来的参数，如果你不想单独处理没哟个参数的话就可以这样写
```
.border_arg(@w:30px,@c:red,@xx:solid){
	border:@arguments;
}
.test_arguments{
	.border_arg()
}
```

##### (7)、避免编译
> 有时候我们需要一些不正确的css语法或者使用一些less不认识的专有语法。要输出这样的值我们可以在字符前加一个~

```
.box{
  widtch:~'calc(100%-80px)'
}

```
##### (8)、!important
```
.test_arguments{
	.border_arg()!important;
}

```



























