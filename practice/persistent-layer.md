# 3层架构-持久层

* 一个数据库表对应一个Dao。
* Dao实现类中不允许含有业务逻辑。
* 查询一行记录用`get`，多行记录用`find`，根据条件查询用`By`。例如：
    * 根据ID查询一个用户，方法名应该叫`getUser($id)`，查询条件为ID时，我们省略`ById`。
    * 根据一批ID查询用户，方法名叫`getUsersByIds(array $ids)`。
* 根据动态条件查询用`search`。例如：
    * 根据动态条件查询用户 `searchUsers($conditions, $orderBy, $start, $limit)`。
* 查询多行记录如果记录集为空则返回`array()`，查询单行记录如果为空则返回`NULL`。
* 记录的添加、更行方法，返回值为被添加、更新的记录。
* 查询多行记录名词用复数，查询单行记录名词用单数。例如：`getUser`, `getUsersByIds`。
* 所有外部传入的参数，必须通过占位符的方式，传入SQL，否则存在被SQL注入的风险。
* 如传入参数是批量的`$ids`时，我们应该：
  ```
  $marks     = str_repeat('?,', count($ids) - 1).'?'; // 生成与id等量个数的占位符
  $sql       = "SELECT * FROM {$this->table} WHERE id IN ({$marks});";
  $rows = $this->getConnection()->fetchAll($sql, $ids);
  ```
* 当有字段需要通过序列化存入时，在dao实现类中声明：
  ```
  private $serializeFields = array(
      'answer' => 'json',
      'metas'  => 'json'
  );
  ```
  在每个查询方法，数据返回时调用：
  ```
  return $row ? $this->createSerializer()->unserialize($row, $this->serializeFields) : null;
  ```
  或
  ```
  return $this->createSerializer()->unserializes($rows, $this->serializeFields);
  ```
  在数据添加/更新时，调用：
  ```
  $fields   = $this->createSerializer()->serialize($fields, $this->serializeFields);
  ```
* 一般情况下所有表都有`id`, `createdTime`, `updatedTime`3个字段，分别表示记录ID、记录的添加时间、记录的修改时间。
  `createdTime`、`updatedTime`的赋值分别由`Dao`的`add`方法和`update`方法把控。

