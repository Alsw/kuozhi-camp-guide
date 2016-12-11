*1* mysql：MySQL sql-mode调整成严格模式

    $sqlInsert = "INSERT INTO users(name, gender, age, profile) VALUES(:name, :gender, :age, :profile)";

*2* 使用命名空间的时候，最好不用require，直接借助User

    require _DIR_.'/controller/controller.php';

*3* app下一层目录均小写命名， 如src。src代码全部放在src目录下，且该目录下文件命名首字母大写。

    app/src/Service
    app/src/Controller
    app/src/Model


*4* 写关于twig的函数修饰符用private

*5* 服务（service）：完整可用的，公共独立的功能块（用户服务，课程服务，小组服务，帖子论坛服务）

    创建如下文件目录，单独存放服务
    Service/User/UserService.php(作为接口)
    Service/User/Impl/UserServiceImpl.php(实现接口的具体逻辑)
    Service/User/Dao/UserDao.php(Dao:与数据库打打交道的类，针对接口编程)
    Service/User/Dao/Impl/UserDaoImpl.php(实现接口的具体逻辑)
    Service/Common/BaseDao.php(实现Connection功能的获取)
    Service/Common/Connection.php（实现与Dao解耦的功能，采用单例模式，保证系统中一个类只有一个实例）


*6* 结对编程

*7* Controller 里面的方法 定义为 xxxAction
##低耦合 高内聚————代码最高境界
##针对接口编程
