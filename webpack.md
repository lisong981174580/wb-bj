
### route

```
<Route path=""  component={}  exact />

path 路径
component  路径匹配成功后组件
exact      路径需要绝对匹配

```

```
('/',{})===
<route exact path='/'  component={} />
('/list',{})===
<route path='/list' component={list}  />

```

###BrowserRouter  本身就是一个容器
```
<BrowserRouter>
  路由
  <Route path='/'  component={Home}  />
  <Route path='/list'  component={List}  />
</BrowserRouter>

```

### 链接
```
<Link  to='/list'></Link>
//匹配后加默认样式
<Navlick  to='/list'  activeClassName=""  activeStyle={{}}/>  <NavLink>
```
### 传参数
```
<Link to="/show/1009">
<Route path="/show/:id"  component={Show} />

Show{
	render(){
	//100dj
	return <div>{this.props.match.params.id}</div>
	}
}

```
```
weather
  --doc
  --src
    --index.jsx
    --components  存放组件  木偶组件
    --containers  存放页面   智能组件
    --configs
    --routes
    --static
       --public.less

```
### html 布局部分
```
a,button{
//去除a 标签和按钮按下的时候的半透明
	-webkit-tap-highlight-color:rgba(0,0,0,0)
}

```


## 环境配置
```
   生产环境依赖： react 、  react-router-dom    react-dom  normalize.css  

   开发环境依赖： webpack  webpack-dev-server style-loader   css-loader    postcss-loader    autofixer
   less  less-loader
   babel-core   babel-loader    babel-preset-latest   babel-preset-react
   url-loader   file-loader

```
##  插件

```
       open-browser-webpack-plugin
       html-webpack-plugin

```
```
   ## 天气app
     ### 路由
       --index   /
       --list    /list
       --add     /add
```