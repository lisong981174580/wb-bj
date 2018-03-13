### echarts中横坐标值显示不全(自动隐藏)解决方案

```
 "xAxis": [{

                gridIndex: 0,
                "type": "category",
                "axisLabel":{
                    interval: 0
                },
                "data": transverseX,
                axisLine: {
                    show: true,
                    lineStyle: {
                        color: 'rgba(144,150,152,1)'
                    }
                },
            }, {
                gridIndex: 1,
                axisLine: {
                    show: false
                },
                axisLabel: {
                    show: false,

                },
                axisTick: {
                    show: false
                },
                splitLine: {show:false}
            }]
            
```