## react 生命周期
> 案例参考地址  https://git.coding.net/lisong181650/weather.git

> 初始化 运行中 销毁 （will、Did）

#### 初始化阶段
> 组建.defaultProps={}    获取默认属性，只执行一次

> 组建.propTypes={}       属性类型检测值

#### 渲染阶段
> componentWillMount(){}   组件将要加载载

> render(){} 组件装载

> componentDidMount(){}     组件装载完成


#### 运行中阶段
>组件props 或 state  修改 触发更新

> componentWillReceiveProps(nextProps){}  属性更新触发

> shouldComponentUpdate(nextProps,nextState){}      属性、状态更改触发决定组件(是否允许更新  return true false)

> componentWillUpdate(nextProps,nextState){}   	   组件将要更新
> render ()	组件更新
> componentDidUpdate(){}         组件更新完成


#### 销毁阶段
> 销毁完成（组件在页面不再使用）

> componentWillUnmount(){}  组件不再使用 会触发，做组件清理工作，清理定时器、事件绑定

#### React 属性和状态
> 属性定义一般为键值对

#### 属性
> 可以接受  初始类型 、引用类型 、组建、扩展运算符

> 在组建内部this.props  获取属性

#### 状态

```
默认
this.state={
	
}

设置
this.setState={
	
}

```

#### 获得DOM节点 
> ReactDOM.findDOMNode()

#### 操作dom
> 只能在componentDidMount(){} 中操作
* 1、ref
* 2、React.findDOMnode(组建)  返回对象

#### React事件
> 两种绑事件的方式

### 方法1：
```
  changecolor(){
	/*只要状态发生改变，就会重新渲染页面*/
    	this.setState({
    		isShow:!this.state.isShow
    	})
    }

	render(){
		/*这里通过display none 控制显示隐藏*/
		this.styles.div.display=this.state.isShow?'block':'none';

		return (
         
            <div>
             <button  onClick={this.changecolor.bind(this)}> 点击出现颜色</button>
             <div  style={this.styles.div} ></div>

            </div>

			)
	}

   也可以把事件处理函数写在组建外面   可以通过
```
### 方法2：
```
componentDidMount(){

		var dom=ReactDOM.findDOMNode(this);
		var button=dom.querySelector('button');
		button.addEventListener('click',()=>{

			this.setState({
				isShow:!this.state.isShow
			})

		})
	}

```

#### 事件
> onContextMenu  鼠标右键

#### 键盘事件  
> 键盘码 e.keyCode

> 事件类型 e.type

#### 处理this
> bind(this,参数，参数...)

#### 添加事件
> 属性上直接ref
> this.refs.btn.addEventListerner();

