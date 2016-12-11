##code review day-two
*  变量命名不能低于三个字符
* 方法要添加访问修饰符，作用域尽量要放低
* 方法{}要换行。


```
    public function()
    {
    }

    private function()
    {
    }

```

* 函数参数变量不要直接修改
* 不要在代码中使用die(),exit()方法
* 单引号和双引号的正确区分使用（双引号会对其内容进行解析，从而时间浪费）
* php文件统一缩进4个空格（和html混写的标签缩进也是4个空格）
* 双引号使用的变量要用{}包起来
* 方法和变量的注释要使用：多行注释



```
        /*
         * @var 
        */    
```

* 确定无用的代码直接删除即可，无需注释
* mysql特殊关键字大写 

```

    $sql = "SELECT * FROM users";
```

* php统一驼峰命名法
* 两个单词的表名命名采用下划线分隔，必须小写。尽量根据英文语义化命名（避免中文拼音）

```
    
    data_user
```

* 已有上下文关系的对象,不要再对其根据上下文意思冗余命名了。
* $e->getLine() ->前后无空格
* require和include区别 
* 数据库中表定义规范

```
    
    CREATE TABLE `users` (
         `id` int(10) unsigned NOT NULL AUTO_INCREMENT COMMENT '系统ID',
         `name` varchar(64) NOT NULL DEFAULT '' COMMENT '姓名',
         `gender` tinyint(1) unsigned NOT NULL DEFAULT '0' COMMENT '0表示未知，1表示男，2表示女',
         `age` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '年龄',
         `profile` text COMMENT '简介',
         PRIMARY KEY (`id`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='用户表'

```

* 一行代码不要过于长，建议使用变量进行重构（具体参见《重构》一书）
* php 开始符 <?php 与结束符(如果只有纯php代码，不用写结束符 ?> )

```
    
    <?php

     public function add() 
     {
     }



```

##day-three额外任务：
*1* 查看php规范：

[php规范](http://gitlab.howzhi.net/tech/knowledge-base/blob/master/coding-standards/php/psr2.md  )  

*2* 下载安装sublime插件phpcs

*3* sql语句注入