# 3层架构 - 视图层

## 路由规范
路由的URL和参数设计遵循REST风格。

#### 基本设计原则：
  * URL表达特定的资源，因此应该用名词描述，不应该出现动词；
  * 使用HTTP请求方法（GET POST PUT DELETE）表达对资源的操作行为，目前不对PUT和DELETE做强制要求；
  * 名词根据需要可以使用层级嵌套；
  * URL终点名词采用复数形式；
  * 额外信息，比如一些查询参数、分页参数可以用?k=v&a=b的形式

#### 特定场景的处理

+ API的多版本
  可以将版本信息写入HTTP header中（比如x-version: 2.1）
  另外也可以加入到URL中。从实践来看，后者好些，github也是这么干的。

+ 依赖URL的权限系统设计
  权限设计中可能把URL＋HTTP METHOD作为权限主体，URL严格遵循层次结构可以缩减权限配置纪录的数目。

+ 资源层次关系较多
  使用别名或者省略一些层次以使URL短些，但慎用。

+ 资源的不同形式
  比如一个表单数据，可能的展现形式有：html、pdf、doc、image等；
  可以把这些信息通过http header表达（自定义x-media-type或者通过content-type指定）；
  也可以用URL表达，比如 order.html order.pdf order.doc ...

#### HTTP响应码参考

在用户发出请求，服务端对请求进行响应时，给予正确的HTTP响应状态码，有利于让客户端正确区分遇到的情况。

* 200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）。
* 201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功。
* 202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）
* 204 NO CONTENT - [DELETE]：用户删除数据成功。
* 400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。
* 401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）。
* 403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的。
* 404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。
* 406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）。
* 410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的。
* 422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误。
* 500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功。

#### HTTP Response约定

* 对于文本信息，如无特殊要求，均使用utf-8编码，json格式；
* 信息应当精简，终端不需要的信息不传递，避免信息层次过多；
* Error 信息的约定？

#### 参考案例

* github
  https://developer.github.com/v3/

## Controller规范

* 按照路由规范中的约定，严格区分GET／POST；
* 所有的web输入参数必须进行校验；
* Controller承接View&Service，不应包含业务逻辑；

## 参考文献

[RESTful API设计指南 －阮一峰](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)