##1.learning

####phpunit 单元测试
####mockery框架：模拟对象 (自行了解）
######当phpunit不够用的时候就可以用mockery

####jenkins工具
######检测单元测试的覆盖率以及定时运行单元测试代码，如果报错就直接提示开发者进行维护
[jenkins](http://jenkins .topxia.com:8000/)

####sonar工具检测代码质量
[sonar](http://jenkins.topxia.com:8888/)

##2.task
* 根据自己的php版本安装对应版本的phpunit

    [安装phpunit安装地址](https://phpunit.de/)
    
        php  --version 查看版本

* Service,Dao,Connection都要写单元测试,用替换依赖来模拟其他的类来传入
* 了解 **持续集成**