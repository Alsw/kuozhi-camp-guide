##silex

*1* url的形式要符合RESTful API的形式

[RESTful参考](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
   
    $app->post('/users');

*2* 挂载是一种组织的方式

[路由配置](http://silex.sensiolabs.org/doc/master/organizing_controllers.html)

*3* view:返回类型； error:异常处理

*4* convert:如果传入的是id ，但是返回的要对象，则用convert进行处理

##symfony:全栈式解决方案

*1* 内置服务器就是一个web server

*2* Nginx 配置文件

[配置参数](http://symfony.com/doc/current/setup/web_server_configuration.html)
    
    server_name :域名
    root:创建的symfony项目目录

    nginx -t 查看配置是否正确

*3* symfony目录框架

    app/AppKernel.php：加载bundle
    Resource :twig寻址机制，首选resource目录下的文件
    src:存放所有的源代码
    vendor:存放第三方代码，因为symfony大量使用了第三方bundle的概念，连自身都是作为一个第三方bundle插件的形式存在。

[symfony文件目录](http://blog.csdn.net/woshiliulei0/article/details/46693793)



##任务
*1* 下载phpMyAdmin

*2* 项目改成基于symfony格式

*3* 了解js模块化管理方式（require.js）

*4* 在symfony基础上引入less,js模块化处理方式

*5* web/asset/less目录存放less代码，web/asset/css