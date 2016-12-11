# 项目实践：用户管理系统（三）

使用MVC模式，改写整个应用程序。

Note:

这时候，程序应改写成：
  * 程序入口文件：`index.php`
  * 用户Modal: `user-modal.php`
  * 用户View：`add-view.html.php`, `edit-view.html.php`, `list-view.html.php`
  * 用户Controller: `user-controller.php`

URL的对应关系：

* index.php?controller=user&action=list 列出用户
* index.php?controller=user&action=add 添加用户
* index.php?controller=user&action=del 删除用户
* index.php?controller=user&action=modify 修改用户