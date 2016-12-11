##code review day-three
*1* gender:设置默认值

![img](图片1.jpg)

*2* empty()代替isset()判断是否为空

*3* 类名首字母大写

*4* 方法和方法之间要换行

    public function getUsersFromTxt()
    {
            $users = file('userDB.txt');
            
            foreach ($users as &$user) {
                    $user = explode('|', $user);
            }

            return $users;
    }

    public function addUser($user)
    {
            $users = file('userDB.txt');
            $userId = count($users)+1;
            $user = $userId.'|'.implode('|', $user)."\n";

            file_put_contents('userDB.txt', $user, FILE_APPEND);
    }

*5* 类名要和文件名一致

*6* 每行代码后面不能有空格

*7* 提交到仓库的代码不能有var_dump()这类调试代码

*8* mysql的语句中的多个参数用"，"(用逗号和空格隔开)
    
     $sql = "INSERT INTO users(name, gender, age, profile) VALUES('{$name}', '{$gender}', '{$age}', '{$profile}')";


*9* 

    <?php

    namespace UserManagerSystem;//不顶格写，无缩进

*10* 更新函数命名一般为update(),不用modify

*11* => , ==操作符前后有空格

    foreach ($user as $key => $value) {
    
    }

*12* 一段逻辑写完换一行

*13* {{ 变量 }} tags一般用{% %} 

*14* Convert Identation to Spaces (sublime右下角调整)


##惩罚记录
* 唐杨：15个俯卧撑
* 吴宗飞：25个俯卧撑
* 李静文：10个俯卧撑

##任务
* bootcamp成员互相测试代码是否能运行成功
* 上传code review 记录到gitlab的bootcamp项目中
* 安装sublime插件DocBlocker
* sql注入问题