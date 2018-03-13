## React项目总结-河洛云管理平台
> 案例参考地址  https://git.coding.net/lisong181650/http-www.51mcee.com.git
### 一、配置文件及环境
> 利用了webpack搭建环境，分生产环境与开发环境，版本选用的是"react": "^15.6.2", "react-dom": "^15.6.2", "react-router-dom": "^4.2.2"，利用补丁，解决了ie上一些兼容问题，并成功兼容到ie8.
#### (1)、package.json（依赖的包）
```
{
  "name": "client_mgr",
  "version": "1.0.0",
  "description": "this is client_mgr",
  "main": "index.js",
  "scripts": {
    "start": "NODE_ENV=development webpack-dev-server --progress --colors",
    "build": "set NODE_ENV=production && webpack --config ./webpack.production.config.js --progress",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "react"
  ],
  "author": "lisong",
  "license": "ISC",
  "dependencies": {
    "antd": "^2.13.11",
    "babel-plugin-import": "^1.6.3",
    "echarts": "^3.8.3",
    "es5-shim": "^4.5.9",
    "normalize.css": "^7.0.0",
    "promise-polyfill": "^6.1.0",
    "react": "^15.6.2",
    "react-dom": "^15.6.2",
    "react-router-dom": "^4.2.2",
    "whatwg-fetch": "^2.0.3"
  },
  "devDependencies": {
    "autoprefixer": "^7.1.4",
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-polyfill": "^6.26.0",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-latest": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "bundle-loader": "^0.5.5",
    "css-loader": "^0.28.7",
    "extract-text-webpack-plugin": "^3.0.0",
    "file-loader": "^0.11.2",
    "html-webpack-plugin": "^2.30.1",
    "less": "^2.7.2",
    "less-loader": "^4.0.5",
    "open-browser-webpack-plugin": "0.0.5",
    "postcss-loader": "^2.0.6",
    "style-loader": "^0.18.2",
    "uglifyjs-webpack-plugin": "^1.1.2",
    "url-loader": "^0.5.9",
    "webpack": "^3.6.0",
    "webpack-dev-server": "^2.8.2"
  },
  "directories": {
    "doc": "doc"
  }
}
```
#### （2）、postcss.config.js
> 自动为CSS3属性添加前缀：
```
module.exports = {
    plugins: [
        require('autoprefixer')
    ]
}

```

#### （3）、webpack.config.js（开发环境配置）
```
var path=require('path');
var webpack=require('webpack');
var htmlWebpackPlugin=require('html-webpack-plugin');
var openBrowserWebpackPlugin=require('open-browser-webpack-plugin');
module.exports={
    devtool: 'inline-source-map',
    // entry:'./src/index.jsx',
    entry: {
        app: [
            path.join(__dirname, 'src/index.jsx')
        ],
        vendor: ['react', 'react-router-dom', 'react-dom']
    },
    output:{
        path:path.join(__dirname,'dist'),//通过HtmlWebpackPlugin插件生成的html文件存放在这个目录下面
        filename:'[name].[hash].js',//编译生成的js文件存放到根目录下面的js目录下面,如果js目录不存在则自动创建
        
          /*
     * chunkFilename用来打包require.ensure方法中引入的模块,如果该方法中没有引入任何模块则不会生成任何chunk块文件
     * 比如在main.js文件中,require.ensure([],function(require){alert(11);}),这样不会打包块文件
     * 只有这样才会打包生成块文件require.ensure([],function(require){alert(11);require('./greeter')})
     * 或者这样require.ensure(['./greeter'],function(require){alert(11);})
     * chunk的hash值只有在require.ensure中引入的模块发生变化,hash值才会改变
     * 注意:对于不是在ensure方法中引入的模块,此属性不会生效,只能用CommonsChunkPlugin插件来提取
     * */
     
        chunkFilename: '[name].[chunkhash].chunk.js',
    },
    resolve: {
        extensions: ['.js','.jsx']
    },
    module:{
        rules:[
            //css解析
            {
                test:/\.css$/,
                loader:"style-loader!css-loader!postcss-loader"
            },
            //less解析  注意要装less
            {
                test:/\.less$/,
                loader:"style-loader!css-loader!postcss-loader!less-loader"
            },
            // jsx解析 babel-core babel-loader babel-preset-latest babel-preset-react
            {
                test:/\.(jsx|js)?$/,
                loader:"babel-loader",
                exclude:/node_modules/,
                query:{
                    presets:['latest','react'],
                    "plugins":[
                        ["import",{"libraryName":"antd","style":'css'}]
                    ]
                },
            },

            //图片解析
            {
                test: /\.(png|jpg|gif|jpeg|bmp)$/,
                exclude:/node_modules/,
                loader: 'url-loader?limit=10000&name=build/images/[name].[ext]'
            },

            //文字解析
            {
                test:/\.(woff|woff2|svg|ttf|eot)($|\?)/i,
                loader:'url-loader?limit=500000'
            }
        ]
    },

    plugins:[
        //生成HTML文件
        new htmlWebpackPlugin({
            template:'./src/index.tmpl.html',
            hash:true
        }),
        new webpack.ProvidePlugin({
            "React": "react",
            "ReactDOM":'react-dom',

        }),
        new webpack.HotModuleReplacementPlugin(),
        new openBrowserWebpackPlugin({
            url:'http://localhost:9090'
        }),
        //为组件和模块分配ID
        new webpack.optimize.OccurrenceOrderPlugin(),
        new webpack.optimize.CommonsChunkPlugin({
            name: 'vendor'
        })
    ],


    // 调用npm install --save-dev webpack-dev-server
     devServer:{
         contentBase: "./build",
         historyApiFallback: true, //不跳转
         inline: true ,//实时刷新
         port:9090,  //端口8080
         hot: true , // 使用热加载插件 HotModuleReplacementPlugin
         host: "0.0.0.0"
    }
}

```

#### (4)、webpack.production.config.js(上线环境配置)
```

/*里面要安装一个css js分离的包*/
const webpack = require('webpack');
const path = require('path');
const htmlWebpackPlugin = require('html-webpack-plugin');
var pkg=require('./package.json');
var CommonsChunkPlugin = webpack.optimize.CommonsChunkPlugin;/*合并公共代码*/
var ExtractTextPlugin = require('extract-text-webpack-plugin');/*分离css与js*/
const UglifyJSPlugin = require('uglifyjs-webpack-plugin');

module.exports = {
    entry:{
        app: [
            path.join(__dirname, 'src/index.jsx')
        ],
        vendor: ['react', 'react-router-dom', 'react-dom']


        // app:"./src/index.jsx",
        // venor:Object.keys(pkg.dependencies)
    },
    output: {
        path: path.join(__dirname, "dist"),
        publicPath:'/',
        filename:'[name].[hash].js',
        chunkFilename: '[name].[chunkhash].chunk.js',

        // filename: "js/[name].js"
    },
    resolve: {
        extensions: ['.js', '.jsx']
    },
    module:{
        rules:[
            //.jsx文件 babel-core babel-loader babel-preset-es2015 babel-preset-react
            {
                test:/\.jsx?$/,
                exclude:/node_modules/,
                loader:'babel-loader',
                query:{
                    presets:['react','es2015'],
                    "plugins":[
                        ["import",{"libraryName":"antd","style":'css'}]
                    ]
                }
            },
            //.css 文件  style-loader css-loader postcss-loader
            {
                test:/\.css$/,
                loader:ExtractTextPlugin.extract({fallback:'style-loader',use:['css-loader','postcss-loader']})
            },
            {
                test:/\.less$/,
                loader:ExtractTextPlugin.extract({fallback:'style-loader',use:['css-loader','less-loader','postcss-loader']})
            },
            {
                test:/\.(png|gif|jpg|jpeg|bmp)$/i,
                loader:'url-loader?limit=10&name=images/[name].[ext]'
            },
            {
                test:/\.(woff|woff2|svg|ttf|eot)($|\?)/i,
                loader:'url-loader?limit=10&name=fonts/[name].[ext]'
            }
        ]
    },
    plugins:[
        new webpack.ProvidePlugin({
            "React": "react",
            "ReactDOM":'react-dom',

        }),
        new htmlWebpackPlugin({
            template: __dirname + "/src/index.tmpl.html",
            hash:true
        }),
        new CommonsChunkPlugin({
            name:'common',
            filename:'js/[name].js'
        }),

        // 优化编译名称
        new webpack.HashedModuleIdsPlugin(),
        new webpack.optimize.CommonsChunkPlugin({
            name: 'runtime'
        }),

        new ExtractTextPlugin('css/[name].css'),
        new webpack.optimize.OccurrenceOrderPlugin(),
        new webpack.optimize.UglifyJsPlugin({
            compress: {
                warnings: false
            }
        }),
        // 定义为生产环境，编译 React 时压缩到最小
        new webpack.DefinePlugin({
            'process.env':{
                'NODE_ENV': JSON.stringify('production')
            }
        }),

        new UglifyJSPlugin()
    ]
}

```
#### (5)、路由配置
> 参考地址 https://github.com/brickspert/blog/issues/#cache ,该路由包含了按需加载的思想
```
/*导入 BrowserRouter ,Route*/
import  {BrowserRouter as Router, Route,Switch,HashRouter}  from  'react-router-dom';

/*按需加载引入Bundle*/
import Bundle from './Bundle';

/*按需加载路径前加
  bundle-loader?lazy&name=login!
  name值最好是问价夹的名字，但千万不要重复
*/
import Login from "bundle-loader?lazy&name=login!../containers/login/index";
import Index from "bundle-loader?lazy&name=index!../containers/index/index";
import BoxDetail from "bundle-loader?lazy&name=boxDetail!../containers/boxDetail/index";
import Organization from "bundle-loader?lazy&name=organization!../containers/organization/index";
import Member from "bundle-loader?lazy&name=member!../containers/member/index";
import Journal from "bundle-loader?lazy&name=journal!../containers/journal/index";
import AlarmList from "bundle-loader?lazy&name=alarmlist!../containers/alarmlist/index";
import Membelinfo from "bundle-loader?lazy&name=membelinfo!../containers/membelinfo/index";
import ChangePass from "bundle-loader?lazy&name=changePass!../containers/changePass/index";
import MonitorEquipment from "bundle-loader?lazy&name=monitorEquipment!../containers/monitorEquipment/index";
import StaffHome from "bundle-loader?lazy&name=staffHome!../containers/staffHome/index";
import Ledger from "bundle-loader?lazy&name=Ledger!../containers/Ledger/index";

import LedgerList from "bundle-loader?lazy&name=ledgerlist!../containers/ledgerlist/index";
import MonitorList from "bundle-loader?lazy&name=monitorlist!../containers/monitorlist/index";


const Loading = function () {
    return <div>Loading...</div>
};

const createComponent = (component) => (props) => (
    <Bundle load={component}>
        {
            (Component) => Component ? <Component {...props}/> : <Loading/>
        }
    </Bundle>
);


/*导入页面
  需要 npm install bundle-loader --save-dev
 
*/
 class Rout extends React.Component {
     constructor(props) {
         super(props);
     }
     render() {
         return (
             <div>
                 <HashRouter basename="/" history={this.props.history}>
                     <div>
                         <Route  exact path='/' component={createComponent(Login)}/>
                         <Route  path='/index' component={createComponent(Index)}/>
                         <Route path='/organization' component={createComponent(Organization)}/>
                         <Route path='/member/:id/:activeortitle' component={createComponent(Member)}/>
                         <Route path='/memberinfo/:id/:activeid/:activeortitle' component={createComponent(Membelinfo)}/>
                         <Route path='/journal' component={createComponent(Journal)}/>
                         <Route path='/changepass' component={createComponent(ChangePass)}/>

                         <Route path='/cindex' component={createComponent(StaffHome)}/>
                         <Route path='/monitorequipment' component={createComponent(MonitorEquipment)}/>
                         <Route path='/monitorlist/:boxid' component={createComponent(MonitorList)}/>
                         <Route path='/boxDetail/:id' component={createComponent(BoxDetail)}/>
                         <Route path='/changepass' component={createComponent(ChangePass)}/>
                         <Route path='/ledger/:id/:kind' component={createComponent(Ledger)}/>
                         <Route path='/alarmlist' component={createComponent(AlarmList)}/>
                         <Route path='/ledgerlist' component={createComponent(LedgerList)}/>
                     </div>
                 </HashRouter>
             </div>
         );

         }


 }

export default Rout;

/*Bundle.js*/
import React, {Component} from 'react'

class Bundle extends Component {
    constructor(props){
        super(props);
        this.state = {
            // short for "module" but that's a keyword in js, so "mod"
            mod: null
        };
    }

    componentWillMount() {
        this.load(this.props)
    }

    componentWillReceiveProps(nextProps) {
        if (nextProps.load !== this.props.load) {
            this.load(nextProps)
        }
    }

    load(props) {
        this.setState({
            mod: null
        });
        props.load((mod) => {
            this.setState({
                // handle both es imports and cjs
                mod: mod.default ? mod.default : mod
            })
        })
    }

    render() {
        return this.props.children(this.state.mod)
    }
}

export default Bundle;

```
### 二、请求数据fetch (data.js)
```
   import config from '../configs/config';
let bodyalert=document.querySelector('.bodyalert');
let bodyalertbtn=document.querySelector('.bodyalertbtn');
bodyalertbtn.onclick=function () {
    bodyalert.style.display='none';
}


export function post({url, body = {}, success}) {
    fetch(config.http + url, {
        method: "POST",
        cache: 'reload',
        headers: {
            "Content-Type": "application/json",
            'Authorization': (sessionStorage.getItem('token') || '')
        },
        body: JSON.stringify(body)
    }).then(function (res) {
        if (res.ok) {
            res.json().then(function (data) {

                if (data.result && data.result.code == 2) {
                    success(data)
                    bodyalert.style.display='block';

                }else if(data.result && data.result.code == 14){
                    
                    if(sessionStorage.getItem('rootstate')=='true'){
                        alert('您的账号被异地登录，请重新登录，点击确认跳转到登录页');
                        sessionStorage.setItem('rootstate','false');
                    }
                    sessionStorage.clear();
                    sessionStorage.setItem('tokenstate','fail')
                    location.reload();


                 }else if (data.result && data.result.code == 0){
                     success(data)
                 }else if(data.result && data.result.code == 13){
                    success(data)
                    console.log('账号或密码错误')
                 }else {
                    success(data)

                }
            })
             console.log("Perfect! Your settings are saved.");
        }else if (res.status == 401) {
            console.log("Oops! You are not authorized.");
        }
    }, function (e) {
        console.log("Error submitting form!");
        console.log('获取数据出错，错误代码');
        console.log(e)
    });
}


export function get({url, success}) {
    fetch(config.http + url, {
        headers: {
            'Authorization': (sessionStorage.getItem('token')  || '')
        }
    }).then(function (res) {
        if(res.ok){
            res.json().then(function (data) {
                console.log(data)
                if (data.result && data.result.code == 2) {
                    success(data)
                    bodyalert.style.display='block';
                }else  if(data.result && data.result.code == 14){

                    if(sessionStorage.getItem('rootstate')=='true'){
                        alert('您的账号被异地登录，请重新登录，点击确认跳转到登录页');
                        sessionStorage.setItem('rootstate','false');
                    }
                    sessionStorage.clear();
                    sessionStorage.setItem('tokenstate','fail')
                    location.reload();
                }else if (data.result && data.result.code == 0) {
                     success(data)
                }else if(data.result && data.result.code == 13){
                    success(data)
                    console.log('账号或密码错误')
                }else {
                    success(data)
                    console.log('获取数据出错，错误代码')
                    console.log(data)
                }
            })
        }else if (res.status == 401) {
            console.log("Oops! You are not authorized.");
        }


    },function (e) {
            console.log("Error submitting form!");
            console.log('获取数据出错，错误代码');
            console.log(e)
        })
}



export function request({url, body = null, success, fail, mode = "postRequest"}) {
    if (mode === 'postRequest') {
        post({
            url: url,
            body: body,
            success: success
        })
    } else {
        // todo get请求
        get({
            url: url,
            body: body,
            success: success
        })
    }
}

```

### 三、解决兼容性问题
#### （1）、ie低版本不支持 fetch、Promise
> 首页index.js引入
```
//引入路由
import Rout from "./router/route";
//引入公共样式css
import 'normalize.css';
import './static/public.less';

import  'whatwg-fetch';
import Promise from 'promise-polyfill';

//es5-shim、babel-polyfill 因为babel在进行编译的时候对于某些属性不能完全编译成es5格式，引入以下两个包可以修补部分不支持的属性
import 'es5-shim';
import 'babel-polyfill';

if (!window.Promise) {
    window.Promise = Promise;
}

ReactDOM.render(<Rout/>,document.querySelector('#root'));

```
#### （2）、解决ie不支持startsWith
> 在低版本ie上不支持startsWith,可以在index.tmpl.html模板文件中手动定义
```
<script>
    if (typeof String.prototype.startsWith != 'function') {
        String.prototype.startsWith = function (prefix){
            return this.slice(0, prefix.length) === prefix;
        };
    }
</script>
```
#### (3)、解决低版本ie不支持forEach
> 在低版本ie上不支持forEach,可以在index.tmpl.html模板文件中手动定义
```
<script>
    if ( !Array.prototype.forEach ) {
        Array.prototype.forEach = function forEach( callback, thisArg ) {
            var T, k;
            if ( this == null ) {
                throw new TypeError( "this is null or not defined" );
            }
            var O = Object(this);
            var len = O.length >>> 0;
            if ( typeof callback !== "function" ) {
                throw new TypeError( callback + " is not a function" );
            }
            if ( arguments.length > 1 ) {
                T = thisArg;
            }
            k = 0;
            while( k < len ) {
                var kValue;
                if ( k in O ) {
                    kValue = O[ k ];
                    callback.call( T, kValue, k, O );
                }
                k++;
            }
        };
    }

</script>

```
> forEach在其他浏览器上只要类似数组的结构就可以使用它遍历，但是在ie上必须是标准的数组类型，因此可以将类似数组的类型强转为数组类型在使用
```
 let findlisbtn = dom.querySelectorAll('.box-find .equipmentCard .equipmentCardtop .title li ');
 
 findlisbtn=[...findlisbtn];
 findlisbtn.forEach=(value)=>{
     
 }
 
```
### (4)、低版本ie不支持其他不明确的属性 
> 如果你要解决ie上的兼容性比如兼容到ie8建议将以下这段代码放在index.tmpl.html中的最前面
```
<script>
    //addEventListener polyfill 1.0 / Eirik Backer / MIT Licence
    (function(win, doc){
        if(win.addEventListener)return;		//No need to polyfill

        function docHijack(p){var old = doc[p];doc[p] = function(v){return addListen(old(v))}}
        function addEvent(on, fn, self){
            return (self = this).attachEvent('on' + on, function(e){
                var e = e || win.event;
                e.preventDefault  = e.preventDefault  || function(){e.returnValue = false}
                e.stopPropagation = e.stopPropagation || function(){e.cancelBubble = true}
                fn.call(self, e);
            });
        }
        function addListen(obj, i){
            if(i = obj.length)while(i--)obj[i].addEventListener = addEvent;
            else obj.addEventListener = addEvent;
            return obj;
        }

        addListen([doc, win]);
        if('Element' in win)win.Element.prototype.addEventListener = addEvent;			//IE8
        else{		//IE < 8
            doc.attachEvent('onreadystatechange', function(){addListen(doc.all)});		//Make sure we also init at domReady
            docHijack('getElementsByTagName');
            docHijack('getElementById');
            docHijack('createElement');
            addListen(doc.all);
        }
    })(window, document);
</script>
```
### 四、解决网站图标加不上去
> 利用工具将其转化为base编码格式放到link标签中的href中,推荐 http://base64.xpcha.com/indexie.php
```
  <link rel="shortcut icon" href="/favicon.ico" type="image/x-icon">
```
### 五、文件目录结构
```
- doc 文档
- README.md 说明文档
- package.json  安装配置文件
- postcss.config.js 自动为css3加前缀
- src
  -- index.jsx 入口文件
  -- index.tepl.html  html模板文件
  -- containers 智能组件
  -- components 木偶组件
  -- lib 公共函数
  -- static 静态文件 
    ---images
    ---publick.less
  -- configs 公共配置文件
  -- fetch 发送请求的文件
     --- data.js
     
- webpack.config.js 开发环境
- webpack.production.config.js 生产环境
- mode_modules 自动生成的
- dist 上线时压缩后的

```

### 六、React音频组件
```
export default class Voice extends React.Component {

    constructor() {
        super()
    }

    render() {
        return <div>
                    <audio src={alarm}   loop={true}  hidden />
               </div>
    }

    componentWillReceiveProps(nextProps) {
        let dom = ReactDOM.findDOMNode(this);
        let audio = dom.querySelector('audio');
        
        // audio
        if (nextProps.start) {
            audio.currentTime = 0;
            audio.play();
        }else{
            audio.pause();
        }
    }

}

```








