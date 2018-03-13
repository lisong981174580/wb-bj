## react深入
### 一、扩展运算符
```
var Display = React.createClass({
        render: function() {
            return(
                    <div>
                        <p>{this.props.color}</p>
                        <p>{this.props.num}</p>
                        <p>{this.props.size}</p>
                    </div>
            );
        }
    });

    var Label = React.createClass({
        render: function() {
            return (
                    <Display {...this.props}/>
            );
        }
    });

    var Shirt = React.createClass({
        render: function() {
            return (
                    <div>
                        <Label {...this.props}/>
                    </div>
            );
        }
    });

    var style={
        color:"steelblue",
        num:"3.14",
        size:"medium"
    }

    ReactDOM.render(

            <div>

                <Shirt {...style} />
            </div>,
        document.querySelector("#container")
    );
```
## 二、直接渲染数组
```
 var Circle = React.createClass({
        render: function() {
            var circleStyle = {
                padding: 10,
                margin: 20,
                display: "inline-block",
                backgroundColor: this.props.bgcolor,
                borderRadius: "50%",
                width: 100,
                height: 100,
            };

            return (
                    <div style={circleStyle}></div>
            );
        }
    });

    var destination = document.querySelector("#container");
   /* var colors = ["#393E41", "#E94F37", "#1C89BF", "#A1D363"];
    var ran = Math.floor(Math.random() * colors.length);

    ReactDOM.render(
            <div>
                <Circle bgcolor={colors[ran]}/>
            </div>,
        destination
    );*/



    var colors = ["#393E41", "#E94F37", "#1C89BF", "#A1D363",
        "#85FFC7", "#297373", "#FF8552", "#A40E4C"];

    var renderData = [];

    for (var i = 0; i < colors.length; i++) {
        renderData.push(<Circle bgcolor={colors[i]} key={i}/>);
    }

    ReactDOM.render(
            <div>
                {renderData}
            </div>,
        destination
    );
```
### 三、时间函数
```
 class Time extends  React.Component{
        constructor(props){
            super(props);
            this.state={
                time:new Date().toLocaleTimeString()
            };
            this.t='';
        }

        Time() {
            this.setState({
                time:new Date().toLocaleTimeString()
            })

        }


        componentDidMount(){
            this.t=setInterval(this.Time.bind(this),1000)
        }


        render(){
            return(
                <div>
                    现在时间是：{this.state.time}
                </div>
            )
        }


    }

    ReactDOM.render(<Time/>,document.querySelector('.time-box'));
```
### 四、避免 ReactRouter 前缀
> 在返回到正常编程进度之前，我们还有一件善后任务。你是否注意到，每一次我们调用由 React Router API 定义的事情时，都要用单词 ReactRouter 作为这件事情的前缀？
```
<ReactRouter.Router>
  <ReactRouter.Route path="/" component={App}>

  </ReactRouter.Route>
</ReactRouter.Router>
```
* 每次调用每个API 都要重复带上 ReactRouter 前缀，显然有点冗长。解决方法是用 ES6 新技巧手动指定哪些值可以自动获得前缀。在 <script> 标记的顶部，添加如下代码：
```
var { Router,
      Route,
      IndexRoute,
      IndexLink,
      Link } = ReactRouter;
```
* 添加了这段代码后，每次我们使用在大括号中定义的值时，在应用运行时前缀 ReactRouter 会自动添加。这意味着我们现在可以回到 ReactDOM.render 方法中，删掉 Router 和 Route 对象前的 ReactRouter 前缀：

```
ReactDOM.render(
  <Router>
    <Route path="/" component={App}>

    </Route>
  </Router>,
  destination
);

```
* 如果在浏览器中预览，最终结果前面的一样。唯一的不同之处是标记更为简洁点。