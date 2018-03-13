---
title: mysql
tags: 李松,2017.6.21,
grammar_cjkRuby: true
---
## 一、什么是数据库
> 是按照数据结构来组织、存储和管理数据的仓库
## 二、myspul
> 数据库管理工具
## 三、表
>
## 四、管理数据库

* 命令
* 图形化界面

## 五、连接数据库
* 配置环境变量

> 我的电脑>高级系统设置>环境变量>系统变量（path)>路径

* 命令:连接数据库
> mysql -uroot -p

* 查看有哪些数据库
> show databases;

* 创建数据库
> create database  库名;
* 选用某一库
>use 库名;

* 看有那些表
> show tables;

* 查看表的结构
> desc 表名;

* 操作

## 六、数据操作语言分类
* DML：对数据进行增删改查；
* DDL:对表进行定义，创建，删除，字段操作；
* DCL:用户权限；

### 数据库语言 DML
> 增删改查

#### 语句：增
>插入那些信息，哪些字段，这些信息所对应的值
```
 insert into 表名 （字段1，字段2） values  (字段1值，字段2值）；
```

* 完整一列
* 部分列  有些虽然没插入，但会有默认值，键值是会自增的
* 是字符串最好加引号
* 完整一行可以简写字段名部分，但后面的值一定要完整的全部写上

```
 insert into 表名  values  (字段1值，字段2值）；
```
* 一次性插入多列，只需将字段值之间加逗号即可；

> 方式1：完整写法
```
 insert into 表名 （字段1，字段2） values  (字段1值，字段2值），(字段1值，字段2值），(字段1值，字段2值）；
```

> 方式2：省略写法
```
 insert into 表名  values  (字段1值，字段2值），(字段1值，字段2值），(字段1值，字段2值）；
```

### 语句：修改
> 修改的是哪些字段，最终值，修改的哪个表，那条数据
```
 update 表名  set 字段1=值1，字段2=值2  where  那一条
```
* 那一条不一定非得是id号，如果用id那么只会改一行
* 修改需要加上条件，如果没有条件，那么会修改所有信息

### 语句：删除
>删除的哪个表，哪一行

```
delete from 表名 where  那一条

```
* 那一条不一定非得是id号，如果用id那么只会改一行
* 修改需要加上条件，如果没有条件，那么会修改所有信息



### 语句：查询

> 怎么查
```
select 字段1，字段2  from  表名  where   expre;

```
>查询整张表
```
select *from user
```
> 查询某一行
```
select *from where  id=2
```
> 查询某一个
```
select name from user  where vid=10;
```
> 查询某个范围

```
select *from where  id=>2;
```
> 查询某个范围的某个字段
```
select name from user  where vid>=10;
```
* 广义投影，两列进行操作


## 模型
>查询 select 运算符

### 条件  where
1.条件表达式为真，则取出
2.比较运算符= ！= >= <= > <
3.like， not like


案例：
* 主键=10；
* 栏目不等于3的  ！=
* 主键>10;  >
* 明年年龄； +
```
select  age+1 form  user;
```
* 栏目为4或者11的  ||  or
* 商品价格范围   and  或者    between   num1    and   num2
* 取id为3或者11   in (3,11)
* 栏目不是3和11的   not in   
* 获取第三栏目下，价格小于1000，或者大于3000，并且点击量大于5
* 价格100-300 或者 2000-5000
* 商品名是以诺基亚开头的
* 商品不是以诺基亚开头的


###  分组 | group by | max min  sum  avg  count |
#### 统计
函数 | 功能
* count()  计算行数
* sum()    求和
* avg()    求平均值
* min()    求最小值
* max()    求最大值


案例：
* 求价格的平均值
* 最贵的、最便宜的
* 求总共有多少种
```
 select count(*) from goods;
```

* 价格总和，并且以he为名字显示出来

```
 select sum(shop_price) as  he from goods;
```

* 商店积压商品的总额
* 商品的最大编号
```
 slect max(goods_id) from goods;
```

* 每个栏目下的平均价格
```
select avg(shop_price) ,cat_id from goods group by cat_id;
```
###  筛选 | having  |
案例：商品价格比市场价格便宜200的
```
 select  shop_price,market_price,market_price-shop_price from goods where market_price-shop_price>200;
```

```
 select  shop_price,market_price,market_price-shop_price  as cha from goods  having cha>200;
```
###  排序 | orderby |
> asc默认为升序    desc降序
```
select  goods_id,doods_name,shop_price from goods order by shop_price desc, goods_id asc;
```
###  限制 | limit   |
> limit  跳过多少条  显示多少条
```
select goods_id,goods_name  from goods limit 0  ,3;
```
* 分页
页码 | limit
1 | limit 0,5
2 | limit 5,5
3 | limit 10,5
n | limit n*(n-1),5


顺序：
where>group by>having>order by>limit

## where的子查询
> 内层查询的结果作为外层查询的条件

* 最新的商品的信息
> 方法1：
```
select *from goods  order by goods_id  desc limit 0,1;
```
>方法二： 先找最大的，然后把最大的作为查询的条件

select  * from goods where goods_id=(select max(goods_id) from goods);


* 每个栏目下最新的商品
>
```
 select *from goods wnher goods_id in(select  max(goods_id) from goods group by cat_id);
```

## from的子查询
> 内存查询的结果当作是一张表
* 找到goods_id 在20~25之间  并且价格大于3000
```
select goods_id, goods_name ,shop_price from(select *from goods where goods_id between 20 and 25) as tmp where shop_price>3000;
```

## exists 子查询

案例：判断当前栏目下是否有商品

```
select *from category where exisit(select *from goods  where  goods.cat_id=category.cat_id);
```
## 内连接 inner join    条件是 on

```
select boy.hid,boy.bname,girl.gname from boy inner join girl on boy.hid=girl.hid;
```
## 外连接
* 左外连接 left join   左边主动找  左边包括左表的所有行，右边匹配不上则默认匹配为空
* 右外连接 right join  右边主动找  右边包括右表的所有行，左边匹配不上则默认匹配为空

```
select  article,title  from   article left join  category  on article.cid=category.cid; 
```
##  union用来连接两个结果集
> 对于相同会合并起来，并且结果集列数必须相等





