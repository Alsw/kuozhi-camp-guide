# 面向对象 - 多态

多态是同一个行为具有多个不同表现形式或形态的能力。

## 引子

UserDao要即可以通过文件存取数据，又可以通过数据库存取数据，我们该怎么做？

```php
class UserDao
{
    public function getUser($id, $source)
    {
        if ($source == 'database') {
            $sql = '....';
            return $this->getDbConnection()->fetch($sql);
        }

        if ($source == 'file') {
            // $user = ....
            return $user;
        }
    }

    public function getUserByName($name, $source)
    {
        if ($source == 'database') {
            // ...
        }

        if ($source == 'file') {
            // ...
        }
    }
}
```
上述做法，虽然实现了需求，但比较挫：

  * 违反了类的单一职责原则，即实现了以DB为数据源的，又实现了以File为数据源。
  * 违反了开闭原则，新增一个数据源时，需要修改原有的代码。

## 多态如何做？

### 定义接口

```php
interface UserDao
{
    public function getUser($id);

    public function getUserByName($name);

    // ...
}
```

### 实现接口

以文件为数据源的实现类：
```
class UserDaoFileImpl implements UserDao
{
    public function getUser($id)
    {
        // ...
    }

    public function getUserByName($name)
    {
        // ...
    }

    // ...
}
```

以数据库为数据源的实现类：
```
class UserDaoDatabaseImpl implements UserDao
{
    public function getUser($id)
    {
        // ...
    }

    public function getUserByName($name)
    {
        // ...
    }

    // ...
}
```

### 使用

```
    // 从文件中取用户
    $userDao = new UserDaoFileImpl();
    <!-- $userDao = new UserDaoDatabaseImpl(); -->
    
    
    $user = $userDao->getUser($id);

```

## 参考资料

  * [多态](https://zh.wikipedia.org/wiki/%E5%A4%9A%E5%9E%8B_(%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%A7%91%E5%AD%A6))