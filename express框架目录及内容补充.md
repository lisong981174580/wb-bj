## 一、文件目录

### bin 入口文件 
    www 启动http服务器 端口
### publish 静态资源目录
    css
    fonts
    images
    js
### routes 模块化路由目录
    index.js
    login.js
### views   模板文件目录
    admin   后台模板
    index   前台模板
### config  公共配置信息
    config
### lib     函数库
    mysql.js
### app.js  项目配置 路由、中间件、模块、错误
### package.json    项目配置信息 命令、依赖文件

---

### 实际上express框架也是一个mvc
> rourer 、module、vews  实际上就是 控制器、模型、视图 mvc

----
### 二、正则取整符号
```
~ 负值
~~ 正值

```
-----

## 三、locals 
> express() 上的一个属性，用于存储信息
- req.locals      只存在与当前这次请求周期中
- app.locals     app实例存在的话，它上面的属性和方法就存在

### 登录验证问题：
> 共两个方向，分别是前端和后台，四种方法  
* 1.验证
    *  前端：
        *  1.利用javascript字符串+正则
        ```
       (1)./^[a-zA-Z]+\w*$]/      用户名
           必须以字母开头。后面可以是 其他字母数字
       (2).html5中表单新增属性     required
       (3).jQuery  Validate插件
        ```

  * 2.后台
     *  做一些数据验证处理

## 四、from表单重要属性
* required  必填属性
* from
```
<from id="myfrom"></from>
<input type="text" form="myfrom" value="">
```


个人中心
  我的信息  头像 昵称 文章列表
  
  首页文章列表