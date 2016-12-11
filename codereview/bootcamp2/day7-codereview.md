##day7codereview

*1*  最好用 $fields 替换 $params 命名

*2* fetchAll() 一次性读多条数据；fetch()读一条数据
    校长忠告：代码中尽量减少if判断条件语句的使用

*3* 命名尽量结合上下文内容命名，不用要类似$data, $flag 这类没有实际意思的变量名。

*4* 接口有时候不能写得过于宽泛，根据实际情况进行条件设置

*5* new static 和 new self 统一规范用self

* self::指向当前的类，如果是父类的话指向的还是自己
* static::最后指向的是子类，会造成代码的混乱

*6* {{ user.id }} 

*7* twig写的html缩进为2个空格

*8* twig block语句分行写

    {% block my_css %}
        ……
    {% endblock %}

*9* codereview 的代码一定要上传到服务器上

*10* 系统项目路径

    app存放配置文件和缓存，日志文件
    bin 存放可执行的二进制文件或者用php可执行脚本
    doc 放文档
    src存放所有的源代码(也存放js，方便开发人员写代码)
    vender 存放第三方库
    web静态资源文件（图片，最后编译成功css，js。app.php作为入口文件也存放在此）

*11*  include后面要空一行
    
    include __DIR__.'/../config/dbConfig.php';
    //空一行
    class UserModel
    {

    }


*12* windows系统sublime开发选择View菜单下的Line Ending 菜单下的Unix


##惩罚
######bootcamp成员没有自我测试成功就提交代码进行codereview，直接赐20个俯卧撑

######唐杨选手：20俯卧撑 （等号没空格；有注释；sql注入；引号内加{}）

    "id={$userId}" 

######李静文选手： 10俯卧撑（没上传服务器， 强制模式下要写对应字段）

##任务
* 单例视频学习
* container学习 [container学习链接](http://pimple.sensiolabs.org/)



