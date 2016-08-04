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

---

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

---

## 3章 对象

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

每个对象都连接到一个原型对象，并从中继承属性。
通过对象字面量创建的对吸纳搞连接到`Object.proprety`，这是js中标配对象。

创建一个对象时，可以选择某个 对象作为原型。

原型连接只有在检索值时候才被用到。如果尝试获取对象的某个属性值，但对象没有该属性名，则会在其原型对象中查找，以此类推，最终抵达`Object.proprety`。如果属性完全不存在于原型链中，则结果为`undefined`，该过程为`委托`。

原型关系是动态的。

### 反射

`typeof` 确定属性类型
`hasOwnProperty` 检测对象是否拥有独有的属性，不会检查原型链

### 枚举

`for in`语句可以用来遍历对象中所有可遍历的属性，属性名出现顺序不确定，包括函数、原型中的属性，可通过`hasOwnProperty`，`typeof`函数来进行筛选

### 删除

`delete` 可以用来删除对象实例的属性，可能会暴露出原型链中的属性

### 减少全局变量污染

javascript可以随意定义全局变量来容纳资源，全局变量削弱了灵活性，可以通过手动创建自定义全局变量，将所用到的内容纳入到这个命名空间，以此避免与其它组件冲突

闭包也可用于信息隐藏，减少全局污染

---

## 4章 函数

函数用于代码复用、信息隐藏、组合调用。用于指定对象行为。编程本身可以理解为将一组需求分解为一组函数与数据结构

### 函数对象

javascript中，函数是对象。
对象是键值对的集合，拥有一个连接到原型对象的隐藏属性`__proto__`，对象字面量连接到`Object.prototype`，函数对象连接到`Function.prototype`（该原型对象本身连接到`Object.prototype`）。
函数创建时配有`prototype`属性，值是一个拥有`constructor`属性且值为该函数的对象，与隐藏的连接到`Object.prototype`属性完全不同

函数是对象，故可以保存在变量、对象、数组，可以作为参数传递给其它函数。函数可以拥有方法。

函数与众不同之处在于他们可以被调用

### 函数字面量

可以通过函数字面量创建函数对象。
```javascript
var add = function(a, b){
    return a + b;
}
```

函数名省略，为匿名函数，函数名可用于递归调用。

函数可定义在其它函数内部，内部函数不仅可以访问自己的参数、变量，还可以访问他所在的父函数的参数、变量。`闭包(closure)`是javascript强大表现力的来源

### 调用

调用函数时，传递控制权、参数给新函数。出声明时定义的形式参数，每个函数还接受两个附加参数：`this`,`arguments`

`this`在面向对象编程中非常重要，值取决于调用的模式。javascript共有4中调用模式：方法调用模式、函数调用模式、构造器调用模式、apply调用模式。不同模式下`this`初始化不同

实际参数与形式参数不匹配时候不会导致运行时错误，无论参数多少都会保存在`arguments`数组中，参数过少时，形参被初始化为`undefined`

#### 方法调用模式

函数被保存为对象的一个属性时，称其为方法，`this`绑定到该对象。可以使用`this`访问自己所属的对象，并从中取值或对对象进行修改。`this`绑定发生在调用时候。通过`this`可取的他们所属对象的上下文的方法成为共哦给你方法。

#### 函数调用模式

当函数并非一个对象的属性时，它被当作一个函数来调用。`this`绑定到全局对象。
```javascript
var a = "window object";
// 没有绑定到对象的函数 this绑定到全局对象window上
var f = function () {
    console.log(this.a);
};
// 一个对对象
var o = {
    a: "inside Object o"
};
// 对象添加另一个方法
o.f2 = function () {
    f();
};
o.f2();         ///////////// window object

// 绑定到对对象 此时this绑定到该对象
o.f3 = f;
o.f3();
```
#### 构造器调用模式

> 本书作者Douglas Crockford，`json`创建者，十分推荐以对象字面量创建对象的方式，以及原型继承，而不推荐以构造方法的形式创建对象，并认为这是迁就基于类的面向对象程序员的举措。

在函数前面使用`new`操作符，则启用构造器模式，将创建一个连接到该构造函数`prototype`成员的新对象，`this`被绑定到这个新对象。

#### apply/call调用模式

`apply`/`call`是函数对象的方法，可以指定`this`值。

`apply`第一个参数是需要绑定的`this`值，第二个参数是一个参数数组。

可用于函数式继承

### 返回

函数总返回一个值，如果没有指定，则为`undefined`
如果函数调用时在前面加上`new`，则如果返回值不是一个对象，则返回`this`（该新对象）

### 异常

```javascript
var add = function (a, b) {
    if(typeof a !== "number" || typeof b !== "number"){
        throw {
            name: "TypeError",
            message: "add need numbers"
        };
    }
    return a + b;
};
(function () {
    try {
        add(32, 'sd'); 
    } catch (error) {
        console.log(error.name);
    }
})();
```

### 作用域

javascript不支持块级作用域，有函数作用域，在函数内部任何位置定义的变量都可以在函数内任何地方访问

最好在函数体顶部声明可能用到的所有变量

### 闭包

函数可以访问它被创建时的上下文，函数嵌套时构成闭包条件

可以用于创建对象私有作用域
```javascript
var myObject = (function () {
    var value = 0;
    return {
        getValue: function () {
            return value;
        },
        increment: function () {
            value++;
        }
    };
} ());
```

```javascript
// 节点元素颜色由黄色渐变为白色
var fade = function (node) {
    var level = 1;
    var step = function () {
        if(level < 16){
            var hex = level.toString(16);
            node.style.backgroundColor = ("#ff" + hex);
            level++;
            setTimeout(function() {
                step();
            }, 300);
        }
    };
    step();
};
fade(document.body);
```

问题
> [循环中的闭包](https://segmentfault.com/a/1190000000471569)
```javascript
// 循环中声明函数 容易产生问题 事由闭包 jslint会提示warning

// 问题常发生在 settimeout 函数/事件绑定 等延迟执行事件
// 绑定的函数执行时 会访问外部环境中的i变量 此时的i已经是循环执行最后以此的i
for (var i = 0; i < 5; i++) {
    setTimeout(function () {
        console.log(i);
    }, 10);
}

// 解决方法之一
// 再次构造一个闭包 将变量i缓存到新函数的变量v中
for (var i = 0; i < 5; i++) {
    var f = function (v) {
        return function () {
            console.log(v);
        };
    };
    setTimeout(f(i), 10);
}
```

### 回调

ajax （Asynchronous JavaScript and XML） 异步javascript与xml技术

向服务器发送同步请求，可能会导致客户端进入假死状态，并在网络或服务器缓慢情况下响应速度过慢
更好的方式是发送异步请求，提供给服务器一个响应到达时即触发的回调函数，客户端不会被阻塞。

### 模块

P40 代码例子不是很懂

### 级联

有些对象没有返回值，则默认为`undefined`,如果让这些方法返回`this`，则启用级联。在一个级联中，可通过单独一条语句调用一个对象的很多方法。
例如在ajax类库中启用级联。

---

## 5章 继承

基于类的与阿眼中，继承提供两个有用的服务，一是代码复用的一种形式（当一个新的类和一个已存在的类大部分相似时，复用可以显著减少软件开发成本），二是引入一套类型系统规范（程序员抚恤编写显式类型转换，从而减少工作量，但会带来安全风险）。

javascript是弱类型语言，对象继承关系变得无关紧要，对于对吸纳该来说重要的是它能做什么，而不是它从哪里来。

javascript提供更为丰富的代码复用模式，可以模拟基于类的模式，并可支持其它更为直接的模式。 javascript中继承模式很多，本书只研究部分简单并优秀的。

基于类的语言中，对象是类的实例，类可以从另一个类继承。 javascript是基于原型，可以从其它对象继承。

### “伪类”

javascript提供通过构造函数产生对象的方法。

每个函数被创建时，函数对象有`prototype`对象属性，该属性包含`constructor`属性，指向这个新创建的函数。

函数化、部件内容不是很懂

## 数组

### 长度

数组含有`length`属性，访问超过数组长度的元素会得到`undefined`，而不是数组越界错误。

`length`赋值为更小的值时，数组多出部分会被省略;设置为更大值时，空余位置会被填上`undefined`。

向数组末尾添加新数据，可以使用`array[array.length]=newValue`或`array.push(newValue)`

### 删除

使用`delete`删除数组元素时候，原位置会留下`undefined`，数组长度`length`不会改变。

使用`splice`可正常移除数组元素。
```javascript
var number = [0, 1, 2, 3, 4];
delete number[4];       //// [0, 1, 2, 3, undefined]
// splice 两个参数分别代表起始位置、要删除的元素个数
number.splice(2, 2);    //// [0, 1, undefined]
```

### 枚举

`for in`可以用于遍历数组所有属性，但无法保证顺序，并可能获得原型链中属性。
使用普通`for`循环+`length`属性等可获得正常的次序
```javascript
var number = [0, 1, 2, 3, 4];
var i ;
for(i = 0; i < number.length; i++){
    console.log(number[i]);
}
```

### 容易混淆的地方 数组类型的选择与判断

区分选择数组与对象：当属性名是小而连续的整数时，使用数组，其它情况使用对象。

判断数组类型：使用`typeof`判断数组得到的是`object`。
书中的方式
```javascript
value && typeof value === "object" && value.constructor === Array
// 也许类似于以下代码
value instanceof Array
```

在识别从不同窗口或帧里构造的数组时会失败，更推荐的方式
```javascript
Object.prototype.toString.apply(value) === "[object Array]"
```





## 9章 代码风格

javascript没有块级作用域，所以建议在每个函数开始部分声明所有变量。

## 10章 优美的特性

- 函数是顶级对象：函数是有此法作用域的闭包
- 基于原型继承的动态对象：对象无类别，可通过普通的赋值给任何对吸纳该添加任何新成员属性
- 对象字面量和数组字面量：方便创建对象和数组。

## 11章 毒瘤

### 全局变量

全局变量在代码规模小的时候会来带一定好处，代码规模增大时，会变得难以管理，降低全局变量的可靠性

声明全局变量的几种方式
- 在任何函数之外放置`var foo=value`
- 给全局变量添加属性`window.foo=value`
- 直接使用未经声明的变量`foo=value`

### 作用域

没有块级作用域，只有函数作用域。因此最好在函数开头部分声明所有变量。

### 自动插入分号

```javascript
return
{
    status:true;
};
// 得到的结果是 undefined

return{
    status:true;
};
// 得到正确结果
```

`return`语句不允许换行

### 保留字 ？

保留字用作对象字面类的键值时，不许被引号扩起来，并且必须使用方括号取值。
建议不要使用保留字做标识符

### typeof

```javascript
typeof null;        //object
typeof /a/;         //object

// 判断是一个对象或数组的方法
if(value && typeof value === "object"){
    // 是对象（或数组 数组也是对象类型）
}
```
### parseInt

```javascript
parseInt("16 tons");    // 16
parseInt("08");         // 可能以8进制解析为0 建议指定进制
parseInt("08", 10);
```

### 浮点数运算精度

```javascript
0.1+0.2;    // 0.30000000000000004
```

### NaN

```javascript
typeof NaN === "number";    // true “不是一个数字”的类型为数字

// 可能产生于将非字符串转化为字符串时
+ "0";         //0
+ "789oops";   //NaN    可与 parseInt对比

// NaN 不等于任何值 包括自己
NaN === NaN;    //false
NaN !== NaN;    //true

// isNaN 用于检验是否为NaN 如果是字符串 则先用+操作符
isNaN(NaN);     //true
isNaN(0);       //false
isNaN("789oop");//true
isNaN("0")      //false

// isFinite 可用于判断是否为数字，会筛选掉NaN和Infinity 但这个函数遇到其它类型时会试图将其转化为数字
// 自定义判断数字类型
typeof value === "number" && isFinite(value);
```

### hasOwnProperty

`hasOwnProperty`只是一个方法，而非运算符。导致其可以被赋值。