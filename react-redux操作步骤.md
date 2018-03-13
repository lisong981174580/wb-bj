#### 1、安装脚手架工具

> npm install  -g create-react-app 

#### 2、安装脚手架

> create-react-app  react-study

> react-study是自己起的名字

#### 3、安装redux

> npm install  redux  —save

#### 4、安装react和redux的连接工具redux-react

> npm install redux-react  —save  

#### 5、使用装饰器优化connect代码

```
Npm run eject(出现配置问件，修改配置文件)
Npm  install babel-plugin-transform-decorators-legacy  --save-dev
```

Packge.json里babel加上plugins配置

```
"babel":{
   "plugins": [
        "babel-plugin-transform-decorators-legacy"
    ] 
 } 
```

#### 6、安装处理异步的工具

> Npm install redux-thunk  —save

#### 7、安装react-router-dom

>npm install react-router-dom —save

#### 8、安装antd第三方库

> npm install antd --save

#### 9、antd中处理按需加载

> npm install  babel-plugin-import —save（按需加载）

并且对package.json做如下配置

```
 "babel": {
     "presets": [
       "react-app"
     ],
     "plugins": [
       ["import", { "libraryName": "antd-mobile", "style": "css"}]
     ]
   },
```

#### 10、Npm install redux-devtools-extension  （至今没有用过）

#### 11、入口文件index.js配置

> const  reduxDevtools=window.devToolsExtension?window.devToolsExtension():f=>f;

#### 12、路由模块

> import {BrowserRouter,Route,Redirect,Switch,Link,HashRouter} from 'react-router-dom';

#### 13、主要模块代码

> Index.js

```
import React from 'react';
import ReactDOM from 'react-dom';

import {createStore,applyMiddleware,compose} from 'redux';
  //createStore 实例化出一个redux对象
  //applyMiddleware开启中间件的工具
  //compose将函数关联起来
  
import {Provider} from 'react-redux'
	//Provider所有内容都在这个组件里面

import thunk from 'redux-thunk';
	//处理异步
	
import reducers from './reducers';
  //所有的规则都引到它里面

import {BrowserRouter,Route,Redirect,Switch} from 'react-router-dom';
import Login from "./containers/login";
import Home from "./containers/home";

const  reduxDevtools=window.devToolsExtension?window.devToolsExtension():f=>f;
const store=createStore(reducers,compose(
    applyMiddleware(thunk),
    reduxDevtools
))
  //createStore 实例化出一个redux对象
  //applyMiddleware开启中间件的工具
  //compose将函数关联起来

ReactDOM.render(
    <Provider  store={store}>
        <BrowserRouter>
            <div>
                <Switch>
                    <Route path='/login' component={Login}></Route>
                    <Route path='/home' component={Home}></Route>
                    <Redirect to='/home'></Redirect>
                    //在switch中每次只会匹配一个，并且是第一个，如果匹配不到，就走重定向了
                </Switch>
            </div>
        </BrowserRouter>
    </Provider>,
    document.querySelector('#root')
)
```

> Reducers.js

```
import {combineReducers} from 'redux';
import {auth} from "./redux/auth.redux";
import {counter} from "./redux/index.redux";
export default combineReducers({auth,counter})
```

> Auth.redux.js

```
const LOGIN='LOGIN';
const LOGOUT='LOGOUT';

export function auth(state={isAuth:false,user:'lisong'},action) {
    switch (action.type){
        case LOGIN:
            return {...state,isAuth:true};
        case LOGOUT:
            return {...state,isAuth:false};
        default:
            return state;
    }
}

export function login() {
    return {type:LOGIN};
}

export function logout() {
    return {type:LOGOUT}
}
```

> Index.redux.js

```
const ADD_NUM='ADD';
const REDUCE_NUM='REDUCE';

export function counter(state=10,action) {
    switch (action.type){
        case ADD_NUM:
            return state+1;
        case REDUCE_NUM:
            return state-1;
        default :
            return state;
    }
}

export function addNum() {
    return {type:ADD_NUM};
}

export function reduceNum() {
    return {type:REDUCE_NUM}
}

export function addNumAsync() {
    return dispatch=>{
        setTimeout(()=>{
            dispatch(addNum())
        },2000)
    }
}
```

> Home.js	

```
import React from 'react';
import Num from "./num";
import {Link,Route,Redirect} from 'react-router-dom';
import List from "../components/list";
import Show from "../components/show";

import {connect} from 'react-redux';
//react和redux关联器
import {logout} from "../redux/auth.redux";

@connect(
    state=>state.auth,
    {logout}
)
//通过这种方法传递状态和方法

class Home extends React.Component{
    render(){
        const match=this.props.match
        const app=(
            <div>
                <h3>home page</h3>
                <button onClick={this.props.logout}>退出登录</button>
                <ul>
                    <li><Link to={`${match.url}`} >首页</Link></li>
                    <li><Link to={`${match.url}/list`}>列表</Link></li>
                    <li><Link to={`${match.url}/show`}>详情</Link></li>
                </ul>

                <Route path={`${match.url}`}  exact component={Num}></Route>
                <Route path={`${match.url}/list`} component={List}></Route>
                <Route path={`${match.url}/show`} component={Show}></Route>

            </div>
        )

        const RedirectLogin=<Redirect to='/login'></Redirect>
        return this.props.isAuth?app:RedirectLogin
    }
}

export default Home;
```

> Login.js

```
import React from 'react';
import {connect}  from 'react-redux';
import {login} from "../redux/auth.redux";
import {Redirect} from 'react-router-dom'

@connect(
    state=>state.auth,
    {login}
)
class Login  extends React.Component{
    render(){
        return(
            <div>
                {this.props.isAuth?<Redirect to='/home'></Redirect>:null}
                <span>login page</span><br/>
                <button onClick={this.props.login}>登录</button>
            </div>
        )
    }
}

export default Login;
```

> Num.js

```
import React from 'react';
import {connect} from 'react-redux';
import {addNum,reduceNum,addNumAsync} from "../redux/index.redux";

@connect(
    state=>({num:state.counter}),
    {addNum,reduceNum,addNumAsync}
)

class Num extends React.Component{
    render(){
        return(
            <div>
                <span>当前数字:{this.props.num}</span><br/>
                <button onClick={this.props.addNum}>加一个</button><br/>
                <button onClick={this.props.reduceNum}>减一个</button><br/>
                <button onClick={this.props.addNumAsync}>过两秒加一个</button>
            </div>
        )
    }
}

export default Num;
```

#### 14、src文件目录

```
-src
 --index.js
 --reducer.js
 --redux
   --auth.redux.js
   --counter.redux.js
 --container.js
   --home.js
   --login.js
   --num.js
 --component
   --list.js
   --show.js
```

