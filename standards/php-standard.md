# PHP代码规范

  [遵守PSR的规范](https://github.com/PizzaLiu/PHP-FIG)

## 代码格式
* 类、方法的括号都得换行。例如：

```
public class CourseService
{
    public function getCourse($id)
    {
        // 业务逻辑
    }
}
```

* 方法体内的代码块的花括号不换行

```
public class CourseService
{
    public function createCourse($id)
    {
        if ($isTeacher){
            // 业务逻辑
        }
    }

    public function findCoursesByIds($ids)
    {
        foreach($coures as $course) {
            // 业务逻辑
        }
    }
}
```

* 缩进使用四个空格。

## 命名
* 命名必须见名知意。如何做好命名？请阅读[命名最佳实践](best-practice/naming-practice.md)。
* 类名需要有修饰符，内部类可以不需要修饰符。
* namespace、类名、接口名尽量使用完整的英文描述符，每个单词首字母大写。

```
namespace Topxia\Service\Question;

public interface QuesionService

public class QuestionServiceImpl
```

* php文件名和类名保持一致。例如：

```
$projectpath/src/Topxia/Service/Question/QuestionService.php
```

* 方法名使用驼峰命名方式，首字母小写，使用『动词+名词』的方式，例如：

```
public function recommandCourse($id)

public function publishCourse($id)

public function createCourse($course)

public function closeCourse($id)

```

* 局部变量、形参命名使用驼峰命名方式，首字母小写，变量都应当以『名词』或者『形容词+名词』的方式命名，例如：

```
$course, $closedCourses, $unusedFiles
```

* 常量命名使用大写，单词间用下划线隔开，例如：

```
const MAX_LIFE_TIME = 3600;
```

## 参考
* 关于php代码的最佳实践可以阅读[Controller最佳实践](best-practice/controller-practice.md)，[Service最佳实践](best-practice/service-practice.md)，[Dao最佳实践]()