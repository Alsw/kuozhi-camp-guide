Javascript 规范
=================

## 文件格式
* 缩进统一用四个空格(spaces4)

## 命名

```javasrcipt
var myVariables = 0;
function myFunctionName(){
	...
}
```
变量名、函数名均采用驼峰式命名规则

## 编程风格

### 1.大括号的位置  

```javascript
/* Bad */	
block
{
	...
}

/* Good */
block {
	...
}
```

绝大多数的编程语言，都用大括号（{}）表示区块（block）。起首的大括号的位置，有许多不同的写法。但是，Javascript要使用后一种，因为Javascript会自动添加句末的分号，导致一些难以察觉的错误。

### 2.调用函数的时候，函数名与左括号之间没有空格。  
### 3.函数名与参数序列之间，没有空格。  
### 4.所有其他语法元素与左括号之间，都有一个空格。  
### 5.不要省略句末的分号  
### 6.不要使用with语句。  

### 7.<code>==</code>   
Javascript有两组相等运算符，一组是==和!=，另一组是===和!==。前者只比较值的相等，后者除了值以外，还比较类型是否相同。
请尽量不要使用前一组，永远只使用===和!==。

### 8.eval  
val用来直接执行一个字符串。这条语句也是不应该使用的，因为它有性能和安全性的问题，并且使得代码更难阅读.
eval能够做到的事情，不用它也能做到。比如
  
```javasrcipt
eval("myValue = myObject." + myKey + ";");
```
　　
可以直接写成 
 
```javasrcipt
myValue = myObject[myKey];
```
　
### 9.单行的块结构
if、while、do和for，都是块结构语句，但是也可以接受单行命令。比如

```javasrcipt  
if (ok) t = true;
```	

甚至写成
  
```javasrcipt 
if (ok)
　　t = true;
```

这样不利于阅读代码，而且将来添加语句时非常容易出错。建议不管是否只有一行命令，都一律加上大括号。  

```javasrcipt 
if (ok){
　　t = true;
}
```

### 10.function语句
在Javascript中定义一个函数，有两种写法：

```javasrcipt
function foo() { }
```

和

```javasrcipt
var foo = function () { }
```

两种写法完全等价。但是在解析的时候，前一种写法会被解析器自动提升到代码的头部，因此违背了函数应该先定义后使用的要求，所以建议定义函数时，全部采用后一种写法。

### 11.基本数据类型的包装对象  
Javascript的基本数据类型包括字符串、数字、布尔值，它们都有对应的包装对象String、Number和Boolean。所以，有人会这样定义相关值：

```javasrcipt
new String("Hello World");
new Number(2000);
new Boolean(false);
```

这样写完全没有必要，而且非常费解，因此建议不要使用。
另外，new Object和new Array也不建议使用，可以用{}和[]代替。

### 12.语句的合并
一些程序员追求简洁，喜欢合并不同目的的语句。比如，原来的语句是

```javasrcipt
a = b;
if (a) {...}
```

他喜欢写成下面这样:

```javasrcipt
if (a = b) {...}
```

虽然语句少了一行，但是可读性大打折扣，而且会造成误读，让别人误以为这行代码的意思是：

```javasrcipt
if （a === b）{...}
```

所以不要将不同目的的语句，合并成一行。

### 13.变量声明
Javascript会自动将变量声明"提升"（hoist）到代码块（block）的头部。

```javasrcipt
if (!o) {
　　var o = {};
}
```

等同于

```javasrcipt
var o;
if (!o) {
　 o = {};
}
```

所以：  
所有变量声明都放在函数的头部  
所有函数都在使用之前定义


### 14.全局变量  
Javascript最大的语法缺点，可能就是全局变量对于任何一个代码块，都是可读可写。这对代码的模块化和重复使用，非常不利。

所以避免使用全局变量；如果不得不使用，用大写字母表示变量名，比如UPPER_CASE。

### 15.new命令  
Javascript使用new命令，从建构函数生成一个新对象。

```javasrcipt
var o = new myObject();
```

这种做法的问题是，一旦你忘了加上new，myObject()内部的this关键字就会指向全局对象，导致所有绑定在this上面的变量，都变成全部变量。

所以不要使用new命令，改用Object.create()命令

如果不得不使用new，为了防止出错，最好在视觉上把建构函数与其他函数区分开来

建构函数的函数名，采用首字母大写（InitialCap）；其他函数名，一律首字母小写。

### 16.自增和自减运算符  
自增（++）和自减（--）运算符，放在变量的前面或后面，返回的值不一样，很容易发生错误。
事实上，所有的++运算符都可以用"+= 1"代替

```javasrcipt
++x
```

等同于

```javasrcipt
x += 1;
```

### 17.字符串
统一使用单引号(')，不使用双引号(")。这在创建 HTML 字符串非常有好处：

```javasrcipt
var msg = 'This is some HTML <div class="makes-sense"></div>';
```

### 18.修改内建对象的原型链

修改内建的诸如 <code>Object.prototype</code> 和 <code>Array.prototype</code> 是被严厉禁止的。修改其它的内建对象比如 <code>Function.prototype</code>，虽危害没那么大，但始终还是会导致在开发过程中难以 debug 的问题，应当也要避免。

### 19.不要使用 switch
switch 在所有的编程语言中都是个非常错误的难以控制的语句，建议用 if else 来替换它。

### 20.三元条件判断（if 的快捷方法）
用三元操作符分配或返回语句。在比较简单的情况下使用，避免在复杂的情况下使用。没人愿意用 10 行三元操作符把自己的脑子绕晕。

```javasrcipt
<!-- 不推荐 -->
if(x === 10) {
  return 'valid';
} else {
  return 'invalid';
}
```

```javasrcipt
<!-- 推荐 -->
return x === 10 ? 'valid' : 'invalid';
```
### 21.数组和对象字面量
用数组和对象字面量来代替数组和对象构造器。数组构造器很容易让人在它的参数上犯错。

```javasrcipt
<!--不推荐-->
var a1 = new Array(x1, x2, x3);
var a2 = new Array(x1, x2);
var a3 = new Array(x1);
var a4 = new Array();
```

正因如此，如果将代码传参从两个变为一个，那数组很有可能发生意料不到的长度变化。为避免此类怪异状况，请总是采用更多可读的数组字面量

```javasrcipt
<!--推荐-->
var a = [x1, x2, x3];
var a2 = [x1, x2];
var a3 = [x1];
var a4 = [];
```

对象构造器不会有类似的问题，但是为了可读性和统一性，我们应该使用对象字面量。

```javasrcipt
<!--不推荐-->
var o = new Object();
 
var o2 = new Object();
o2.a = 0;
o2.b = 1;
o2.c = 2;
o2['strange key'] = 3;
```

```javasrcipt
<!--推荐-->
var o = {};
 
var o2 = {
  a: 0,
  b: 1,
  c: 2,
  'strange key': 3
};
```

### 22.this 关键字
只在对象构造器、方法和在设定的闭包中使用 this 关键字。this 的语义在此有些误导。它时而指向全局对象（大多数时），时而指向调用者的定义域（在 eval 中），时而指向 DOM 树中的某一节点（当用事件处理绑定到 HTML 属性上时），时而指向一个新创建的对象（在构造器中），还时而指向其它的一些对象（如果函数被 <code>call()</code> 和 <code>apply()</code> 执行和调用时）。

正因为它是如此容易地被搞错，请限制它的使用场景：

* 在构造函数中
* 在对象的方法中（包括由此创建出的闭包内)

[更多规范](http://124.160.104.74:5000/)