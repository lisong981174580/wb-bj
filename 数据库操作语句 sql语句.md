---
title: 数据库操作语句 sql语句
tags: 李松,模板,
grammar_cjkRuby: true
---

###  一、查询
>从哪里（表），查询什么数据
```
    SELECT * FROM `student` //不分大小写  从student表查询所有信息
    SELECT name,sex from `student`
```
### 二、修改
>修改的是那张表，那条数据，那个字段   更新   设置  地点
```
UPDATE `ww1702`.`student` SET `sex` = 'nv' WHERE `student`.`id` = 1;
```

### 三、删除
>删除哪个表里的哪条
```
DELETE FROM `ww1702`.`student` WHERE `student`.`id` = 2
```

### 四、添加
>那个表，哪些字段，这些信息所对应的值
```
INSERT INTO `ww1702`.`student` (`id`, `name`, `sex`, `arg`, `pro`, `jg`) VALUES (NULL, '李松', '男', '20', '机械', '山西');

//或者

insert into student (name, sex)  values  ('李松', '男')

```