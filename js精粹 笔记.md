# javascript精粹

## 1章 精华

优秀的部分：函数、弱类型、动态对象、对象字面量表示法
糟糕点想法：基于全局变量、编程模型

js函数基于语法作用域的顶级对象
js是第一个成为主流点lambda语言，相对于java，与lisp、scheme有更多相同点，是披着c外衣点lisp

强类型，允许编译器在编译时检查错误，便于尽早修复，付出较小的修复代价

对象字面量表示法，通过列出对象的组成部分，可以简单的创建出对吸纳搞，是json灵感来源

原型继承，具有争议的特性，js有一个无类型点对象系统，对象直接从其它对象中继承属性，对于食用类创建对象的程序员来说有点难以理解

依赖于全局变量进行连接，相当糟糕的特性，编译单元的顶级变量被附加到全局变量的公共空间，有缓解这个问题的方法

支持Lambda函数，既匿名函数

## 2章 语法

标识符用于语句、变量、参数、属性名、运算符、标记

### Number 64位 

NaN是一个数值，表示不能产生正常的运算结果，不等于任何值，包括自己，

```javascript
NaN === NaN //false
typeof NaN  //number
isNaN(3)    //检测NaN
```

Infinity 无穷大

Math常用方法  ceil 向上舍入  floor 向下舍入  round 四舍五入

### 字符串 16位字符（UTF-8）

### 语句

可以被转化为false的值：
- null
- undefined
- false
- 0
- NaN
- ''

"false"字符串被转化为true

### 表达式

 前置运算符 prefix operator
 - `typeof`
 - `+` 转化为数字
 - `-` 数字取反
 - `!` 布尔值取反

typeof 运算符产生的值： undefined boolean number string function object

```javascript
typeof null //object
```

运算符优先级 (反斜杠是针对markdown的转义)：

1. . [] ()
2. delete new typeof + - !
3. \* / %                   
4. \+ -
5. \>= <= > <
6. === !==
7. &&
8. ||
9. ?:

中缀运算符 infix operator
- `+` 数字加法/字符串拼接
- `/` 数字除法运算，即使整数相除也可能得到小数
- `||` 第1个运算数值为真->第1个运算数 否则下一个运算数 返回值不一定为boolean 可用于设置默认值
- `&&` 第1个运算数值为假->第1个运算数 否则下一个运算数 返回值不一定为boolean 可用于避免从`undefined`属性值中取值导致的`TypeError`异常

### 字面量

对象字面量，是一种可以方便按制定规则创建对象点表示法，属性名是标识符或字符串，属性名被当作字面量而不是变量，属性名只有在编译时候才知道（`with`抛出异常的原因）

## 对象

js数据类型
- 基本数据类型：null, undefined, boolean, number, string
- 对象(数组、函数、正则表达式、对象等)

对象是属性容器，每个属性有名字、值，名字是包括空字符串在内的任意字符串，名字是除了`undefined`以外任何值

js中对象是无类型(class-free)的，对新属性的名字、属性值无限制，适用于汇集、管理数据
对象可以包含其它对象，故容易表示成树状和图形结构

### 检索

`||` 可用于设置默认值
`&&` 可用于避免从`undefined`属性值中取值导致的`TypeError`异常

```javascript
var a = {x: 3};
a.status || "unknown";  //默认值 unknown 在无法取得属性时候
a.status;               //undefined
a.status.x;             //TypeError
a.status && a.status.x; //undefined
```

### 原型

每个对象都连接到一个原型对象，并从中集成属性。
通过对象字面量创建的对吸纳搞连接到`Object.proprety`，这是js中标配对象。

创建一个对象时，可以选择某个 对象作为原型。

原型连接只有在检索值时候才被用到。如果尝试获取对象的某个属性值，但对象没有该属性名，则会在其原型对象中查找，以此类推，最终抵达`Object.proprety`。如果属性完全不存在于原型链中，则结果为`undefined`，该过程为`委托`。

p22