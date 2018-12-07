---
title: PHPCMS常见问题
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

## 1、页面主要结构
* 主页面 index
  * category  分类页
  * list 列表页
  * 详情页  show

## 2、操作方法

> 建库、网站名称

* 网页标题： 网页标题是建库的时候就写好了，不能改   包括一些关键字
* 建库方法：将phpcms_v9_UTF8文件放到www目录中，修改名称，从index.html进入，直接通过网页导航下载，安装以及建库

> 管理栏目、添加子栏目、管理文章  

* 分别对应 category、list、show 按照一定的规则可以引入到页面中

* 提供了很多模版，只需要以相同的名称改内容即可
* 如果模版不够，如列表页不是相同的模版，则只需再复制相应的模块加后缀便可
* 如果不知道输出字段信息，可以用var_dump（）输出



## 常见问题

> 字段不够

* 在模型管理中添加字段或者修改字段
> 协同开发

* 为了防止字段冲突，可以新添加一个模型，然后合并起来即可  只需最终将数据库合并即可


## 路径问题

* APPPATH  根路径

## 变量

* get_siteid()：获取当前站点id
* {siteurl($siteid)} 网站的url

## 代码解读
> 网页标题  

```
<title>{if isset($SEO['title']) && !empty($SEO['title'])}{$SEO['title']}{/if}{$SEO['site_title']}</title>

```


> 推荐位部分

```
<!--推荐位部分-->
    <div class="content">
    {pc:content  action="position" posid="9" order="id" num="10" cache="3600"}
    		<div id="announ">
                 <ul>
                 {loop $data $k $v}
                      <li><a href="{$v[url]}">{$v[title]}</a></li>
                      {/loop}
                 </ul>
            </div>
     {/pc}
	 {php echo runhook('glogal_header')}
```

> rss

```
	<!--rss-->
				<a href="{APP_PATH}index.php?m=content&c=rss&siteid={get_siteid()}" class="rss ib">rss</a>

```

> 登录注册
```
	<!--登录注册-->
				<span class="rt">
					<script type="text/javascript">document.write('<iframe src="{APP_PATH}index.php?m=member&c=index&a=mini&forward='+encodeURIComponent(location.href)+'&siteid={get_siteid()}" allowTransparency="true"  width="500" height="24" frameborder="0" scrolling="no"></iframe>')</script>
				</span>
				
```
> 搜索部分

```

<!--搜索部分-->
    <div class="search">
    	<div class="tab" id="search">
			{php $j=0}
			{php $search_model = getcache('search_model_'.$siteid, 'search');}
			{loop $search_model $k=>$v}
			{php $j++;}
				<a href="javascript:;" onclick="setmodel({$v['typeid']}, $(this));" style="outline:medium none;" hidefocus="true" {if $j==1 && $typeid=$v['typeid']} class="on" {/if}>{$v['name']}</a>{if $j != count($search_model)}<span> | </span>{/if}
			{/loop}
			{php unset($j);}
		</div>

```

> 表单部分
```
	<!--表单部分-->
        <div class="bd">
            <form action="{APP_PATH}index.php" method="get" target="_blank">
				<input type="hidden" name="m" value="search"/>
				<input type="hidden" name="c" value="index"/>
				<input type="hidden" name="a" value="init"/>
				<input type="hidden" name="typeid" value="{$typeid}" id="typeid"/>
				<input type="hidden" name="siteid" value="{$siteid}" id="siteid"/>
                <input type="text" class="text" name="q" id="q"/><input type="submit" value="搜 索" class="button" />
            </form>
        </div>
    </div>
    
```


## 补充部分
* 1、安装phpcms
* 2、使用phpcms  
    *content内容板块

## 网站结构
* 上衣咨询
    * 新闻
        * 国内新闻
        * 国际新闻
    * 财经
        * 宏观
        * 理财
    * 体育
        * nba
        * cba
    * 科技
        * 历史 
        * 文化
    * 星座
    
 
## 轮播图
swiper
* 1、新建一个隐藏栏目
* 2、推荐位



## 首页公司简介
## 网站底部版权信息
## 友情链接


## 底部导航 
* 公司简介   单网页  没有
* 新闻中心   外部链接  有
* 招聘简章   栏目   没有
* 联系我们   单网页  没有


## 版权信息
compny  公司名
number  备案号
tel:  电话
tel400  400电话
email   邮箱
copyright    版权服务器期限



moreinfo="1"















