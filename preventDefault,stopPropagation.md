## javascript阻止事件冒泡和浏览器的默认行为
> 在使用javascript编程时会遇到一个问题,就是当你给html添加事件时,由于浏览器默认的为冒泡型事件触发机制,所以会触发你不想触发的事件.那么通过如下的函数可以解决这个问题.[兼容IE和FF]

### 1.阻止事件冒泡,使成为捕获型事件触发机制.
```
function stopBubble(e) { 
//如果提供了事件对象，则这是一个非IE浏览器 
if ( e && e.stopPropagation ) 
    //因此它支持W3C的stopPropagation()方法 
    e.stopPropagation(); 
else
    //否则，我们需要使用IE的方式来取消事件冒泡 
    window.event.cancelBubble = true; 
}

```
### 2.当按键后,不希望按键继续传递给如HTML文本框对象时,可以取消返回值.即停止默认事件默认行为.
```
//阻止浏览器的默认行为 
function stopDefault( e ) { 
    //阻止默认浏览器动作(W3C) 
    if ( e && e.preventDefault ) 
        e.preventDefault(); 
    //IE中阻止函数器默认动作的方式 
    else
        window.event.returnValue = false; 
        return false; 
}
 
 ```

那么通过下面的一段代码我们来看下函数一的效果:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
 
<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<title>效果测试</title>
<script language="javascript" type="text/javascript" src="jquery-1.4.2.js"></script>
<script language="javascript" type="text/javascript">
$(document).ready(function()
{
$('div.c1').click(function(e){alert('单击了div');});
$('div.c2').click(function(e){alert('单击了div');stopBubble(e);});
$(document).click(function(e){alert('单击了document');});
$('#txt1').val('123');
$('#txt1').click(function(e){stopBubble(e);});
$('#txt1').keydown(function(e){stopDefault(e);alert('你按下了键值'+e.keyCode); });
})
 
function stopBubble(e) { 
//如果提供了事件对象，则这是一个非IE浏览器 
    if ( e && e.stopPropagation ) 
    //因此它支持W3C的stopPropagation()方法 
    e.stopPropagation(); 
     else 
    //否则，我们需要使用IE的方式来取消事件冒泡 
    window.event.cancelBubble = true; 
} 
//阻止浏览器的默认行为 
function stopDefault( e ) { 
    //阻止默认浏览器动作(W3C) 
    if ( e && e.preventDefault ) 
        e.preventDefault(); 
    //IE中阻止函数器默认动作的方式 
    else 
        window.event.returnValue = false; 
    return false; 
}
</script>
<style type="text/css">
body{
font-size:14px;
    }
}
.c1{
    font-family:"Arial Unicode MS"
    }
.c2{
    font-family:helvetica,simsun,arial,clean
    }
</style>
</head>
 
<body>
 
<div class="c1">测试的文字,这里是样式C1,单击以冒泡的形式触发事件.</div><hr/>
 
<div class="c2">测试的文字,这里是样式C2,单击以捕获的形式触发事件.</div><hr/>
 
<div><input id="txt1" name="Text1" type="text" /></div><hr/>
 
</body>
</html>
```