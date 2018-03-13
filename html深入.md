## html深入

### 一、网页宽度自动适应手机屏幕宽度的方法
```
//本人常用的
 <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
 
 ```
 ```
 <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=0.5, maximum-scale=2.0, user-scalable=yes" />  
 在网页的<head>中增加以上这句话，可以让网页的宽度自动适应手机屏幕的宽度。

其中：

width=device-width ：表示宽度是设备屏幕的宽度
initial-scale=1.0：表示初始的缩放比例
minimum-scale=0.5：表示最小的缩放比例
maximum-scale=2.0：表示最大的缩放比例
user-scalable=yes：表示用户是否可以调整缩放比例

如果是想要一打开网页，则自动以原始比例显示，并且不允许用户修改的话，则是：

<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no" />  

 这样子写后，就可以把一些页头横幅等的图片的宽度都设置成style="width:100%"，整个页面在设备上看起来就是全屏的了。
 
 ```
 ### 二、disabled用法
 >   value.setAttribute("disabled","disabled")
 ```
ledger_input.forEach((value)=>{
    value.setAttribute("disabled","disabled")
})
                
                
ledger_input.forEach((value)=>{
    value.removeAttribute("disabled")
})

  ```
  
  ### 三、窗口针技术iframe
  ```
  <a href="http://www.51mcee.com/about.html" target="nm_iframe">关于我们</a>
<iframe id="id_iframe"  name="nm_iframe"  src="https://port.51mcee.com:4380/report/entry/daily.html?token=TOKEN-EE7A5DBACD68-d1c735&boxId=5a3082361b6b12cecad753cc&port=16842752&entry=285278213"></iframe>
```

### 四、react中表单验证使用正则pattern
```
import React from 'react';
import {connect}  from  'react-redux';
import {login} from "./Auth.redux";
import {Redirect} from 'react-router-dom';

//处理两个reducer,每个reducer都有一个state
//合并reducer
@connect(
    state=>state.auth,
    {login}
)

class Auth extends  React.Component{
    render() {
        console.log(this.props)
        return (
            <div>
                {this.props.isAuth ? <Redirect to='/dashboard'></Redirect> : null}
                <div>您暂时没有权限，需要登录才能看到</div>
                <form   action=""  method="post"  target="nm_iframe"  onSubmit={this.onSubmit.bind(this)}>
                    <div className='input_box'>
                         <label htmlFor='name' >用户名：</label>
                        <input type="text"  id='name'    required/>
                    </div>

                    <div className='input_box'>
                        <label htmlFor='password'>密码：</label>
                        <input type="password"    id='password' pattern="[A-z]{3}" required/>
                    </div>

                    <div className='input_box'>
                        <input type="submit"  />
                    </div>
                </form>
                <iframe  name="nm_iframe"  title='iframe' style={{display:'none'}}></iframe>
            </div>
        )
    }
    onSubmit(){
        this.props.login();
    }
}

export default Auth;

```
### 五、解决跨域
```
var cors=require('cors');
var app =express();
app.use('*', cors({ origin: '*' })); // 注意：这里要修改成客户端的端口

```
 ### 六、防止浏览器记住密码后自动填充
 > 记住密码在默认情况下，记住的是password类型的表单以及与他相邻的非input的表单的内容，所以此方法是为了迷惑浏览器，只需要在他前面加上一个类型type和name相同的inpu便可
 
```
<input type="password" name='password'   style={{display:'none'}}/>
<input type="password"  name='password' autoComplete="off" />

```
### 七、阻止input在自动填充的时候出现难看的黄色背景
> 使用chrome浏览器选择记住密码的账号，输入框会自动加上黄色的背景，有些设计输入框是透明背景的，需要去除掉这个黄色的背景；
```

input:-webkit-autofill {
  -webkit-box-shadow: 0 0 0 1000px white inset !important;
}

```

### 八、禁止谷歌浏览器自动翻译
```
 <meta name="google" content="notranslate" />
 
 ```
 
### 九、阻止事件冒泡
```
  <td>
     { sessionStorage.getItem('management')
        && <div className="td_img"
              onClick={(e)=>{
                  e.stopPropagation();
                  e.nativeEvent.stopImmediatePropagation();
                  this.onDeterDisplay(value.id)}
              }>
             <div className="img"/>
             <span>删除</span>
         </div>
     }

 </td>
 ```
 
 ### 十、react音频组件
 ```
 import alarm from '../../../containers/boxDetail/audio/6175.mp3'

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
### 十一、三角形写法
```
.sanjiao {
 width: 0;
 height: 0;
 overflow: hidden;//处理ie最小高度问题

 border-width: 10px;
 border-color: red transparent transparent transparent;

 border-style: solid dashed dashed; dashed;//兼容ie
}

```