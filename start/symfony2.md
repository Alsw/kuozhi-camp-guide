#Symfony2简介


## Symfony2是做什么的？

使用原生的PHP进行Web开发时，应对客户端的请求，通常是一个请求对应一个PHP脚本，使用 ```$_REQUEST、$_POST```等提取HTTP数据，使用PDO建立数据库连接、CURD、关闭连接。
Symfony2作为MVC框架，大大简化了这些操作，Symfony的Controller组件让我们可以在一个PHP脚本（类）中定义对多个请求的处理方法，请求的参数直接作为参数传递给方法，同时对Request、Response进行封装，代码更简介优雅，
结合Twig，前后端有效分离，开发效率更高。其Doctrine组件对Dao层进行封装，我们可以只关心自己的业务逻辑而不必考虑数据库连接的创建关闭，同时其提供的连接池也提高了数据库操作效率。

## Symfony2 简介

* 由于Symfony比较庞大，建议按以下方式起步：
[安装Symfony](http://symfony.com/doc/current/book/installation.html)
[Symfony最佳实践](http://symfony.com/doc/current/best_practices/index.html)

* 如果已经有一定了解则可以进一步学习Symfony的组件体系：
[Controllers](http://symfony.com/doc/current/book/controller.html)
[Routing](http://symfony.com/doc/current/book/routing.html)
[Templating by Twig](http://symfony.com/doc/current/book/templating.html)
[Configuration](http://symfony.com/doc/current/book/configuration.html)
[Bundles](http://symfony.com/doc/current/book/bundles.html)
[Doctrine](http://symfony.com/doc/current/book/doctrine.html) or [Propel](http://symfony.com/doc/current/book/propel.html)
[Testing](http://symfony.com/doc/current/book/testing.html)
[Validation](http://symfony.com/doc/current/book/validation.html) (由于需要对Bean对象化，而且基于注释，比较麻烦，目前不推荐，了解即可)
[Forms](http://symfony.com/doc/current/book/forms.html) (了解即可)
[Security](http://symfony.com/doc/current/book/security.html)
[HTTP Cache](http://symfony.com/doc/current/book/http_cache.html)
[Translations / i18n](http://symfony.com/doc/current/book/translation.html)
[Service Container](http://symfony.com/doc/current/book/service_container.html)
[Performance](http://symfony.com/doc/current/book/performance.html)
[Cookbook / FAQ](http://symfony.com/doc/current/cookbook/index.html)

* Silex 
  作为Symfony的迷你版，上手更容易些，有兴趣的可以自己研究一下，链接：[Silex官网](http://silex.sensiolabs.org/)

## 拓展阅读

* [Symfony 官网](http://symfony.com/)