# express
Express 是一个基于 Node.js 平台的极简、灵活的 web 应用开发框架，帮助你创建各种 Web 和移动设备应用。

## Express 框架核心特性：
- 模板解析
- 静态文件服务
- 中间件
- 路由控制

### 安装

```
npm install express
```

### 路由控制
通过不同的URL访问指定的页面

路由（Routing）是由一个 URI（路径）和一个特定的 HTTP 方法（GET、POST等）组成的，涉及到应用如何响应客户端对某个网站节点的访问。

```
app.METHOD(PATH, HANDLER)
```
METHOD 是http方法：
- get  查，获取资源,
- post 增，给服务器新增一个资源,新资源的建立
- put  改,对已有资源的修改
- delete 删,请求服务器删除制定的资源
- all   所有http请求方式都会匹配成功

PATH 是匹配的路径；
HANDLER 路由匹配成功执行的回调函数。

```
app.get('/index', function (req, res) {
  res.send('这是get请求')
});
```
## 路径中路径部分

- 字符串
- 字符串模式 ？ + * （）
- 正则

## 静态文件引入
```
app.get('/',function (req,res) {
    res.sendFile(__dirname+'/index.html')
});
app.listen(8000,'localhost')
```
### 静态资源文件的访问
```
app.use(express.static('public'));
```
### 虚拟路径
```
app.use('/static', express.static('public'));
```



## 中间件express.static(root, [options])

中间件就是处理HTTP请求的函数 ，用来完成各种特定的任务
- 检查用户是否登录
- 添加公共方法

一个中间件处理完，可以把相应数据再传递给下一个中间件。 如果调用回调函数的 next 参数表示将请求数据传递给下一个中间件。

app.use([path], function(request, response, next){}); //可选参数path默认为"/"

## request 获取请求参数
- req.host返回请求头里取的 主机名 (不包含端口号)。
- req.path返回请求的URL的 路径名 。
- req.query是一个可获取客户端get请求 查询字符串 转成的对象，默 认为{}。
- req.params是一个由 路径参数 组成的对象。

## send()向浏览器发送响应,并可以智能处理不同类型的数据


## 模板

### 指定渲染模板引擎
app.set('view engine', 'ejs');

## Express 应用生成器
通过应用生成器工具 express可以快速创建一个应用的骨架。

npm install express-generator -g

-h 选项可以列出所有可用的命令行选项

### 文件结构
- app.js : 入口文件
- package.json : 工程信息以及模块依赖 通过npm安装模块时输入命令 : npm instal xxx –save , 会自动把模块信息保存在package.jason中
- node_modules : 存放模块
- public : 存放image , css , js 等文件
- routes : 存放路由文件
- views : 存放视图文件
    如jade,ejs,html等(个人使用jade)

    
## 模板引擎
模板引擎是一个将页面模板和要显示的数据结合起来生成HTML页面的工具

### ejs的标签
- <% 'Scriptlet' 标签, 用于控制流，没有输出

- <%= 向模板输出值（带有转义）

- <%- 向模板输出没有转义的值

- <%# 注释标签，不执行，也没有输出

- <%% 输出字面的 '<%'

- %> 普通的结束标签




