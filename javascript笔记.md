# javascript

## 相关标签

`<script>` 之间可插入脚本代码，可放入`<head>`或`<body>`中

`<script src="">` 可引入外部脚本

---

## 常用函数

### 输出
```javascript
document.write("");
```

### 获取元素
```javascript
document.getElementById("");
```

### 弹出提示框
```javascript
alert("");    
```

### 日志信息打印

```javascript
console.log("Log level");
console.debug("Debug level");
console.info("Info level");
console.warn("Warn level");
console.error("Error level");
```

---

## 运算符

### `===`

`===` 类型和值都相同才为`true`

```javascript
"10" == 10  //true
"10" === 10 //false 与 !== 相对
```

## 循环

### forEach
```javascript
var a = [1, 2, 3, 4];
for(var i in a){                //i 相当于下标
    document.write(a[i] + "<br/>");
}
```

---

### 函数

### 定义
```javascript
function demo(a, b){}
```

### 调用

1. `<script>`中直接调用

```javascript
alert("hello");
```

2. `html` 中javascript事件，如`onclick`函数

```html
<button onclick="alert('hello')">click me</button>

<input type="button" onclick="alert('hello')" value="click me">
```

### 全局/局部变量 
```javascript
var m = 1;      //全局变量
n = 2;          //全局变量
function demo(){
    var x = 3;  //局部变量
    y = 1;      //全局变量
}
```

---

## 异常处理
```javascript
try{
    alert(str);
}
catch (err){
    console.error(err);
}
```

```javascript        
function checkEmpty(){
    try{
        var text = document.getElementById("txt").value;
        if(text == ""){
            throw "username is empty";
        }
    }
    catch (err){
        alert(err);
    }
}
```

## javascript 事件

### `onclick` 点击事件

### `onmouseover` 鼠标移入

### `onmouseout` 鼠标移出

### `onchange` 文本内容发生变化（焦点变动时检测）

### `onselect` 文本选中

```html
<input type="text" id="txt" onselect="selectEvent(this)">
<script>
    function selectEvent(ele) {
        ele.style.backgroundColor = "red";
    }
</script>
```

### `onfocus` 光标聚焦

### `onblur` 光标移开

### `onload` 网页加载（常用于`body`）

### `onunload` 网页关闭

## DOM

### 改变输出流

```javascript
document.wirte();
```

### 寻找元素

```javascript
document.getElementById("");
```

### 改变html内容

```javascript
document.getElementById().innerHTML = "";
```

### 改变html属性

```javascript
document.getElementById("aid").href = "http://sina.com";
```

### 改变css属性

```javascript
document.getElementById("colorfulDiv").style.backgroundColor = "red";
```

### 添加/移出事件句柄

```javascript
btn.addEventListener("click", hello);
btn.addEventListener("click", world);
btn.removeEventListener("click", hello);
function hello() {
    alert("hello");
}
function world() {
    alert("world");
}
```

### dom属性

- `nodeType` 节点类型

    1 Element 代表元素
    2 Attr 代表属性
    3 Text 代表元素或属性中的文本内容

- `nodeName` 节点名字

### 详解-控制html

1. `getElementsByName()` 通过name

2. `getElementsByTagName()` 通过标签

3. `getAttribute()` 获取元素属性

4. `setAttribute()` 设置元素属性

5. `childNodes()` 访问子节点（得到子节点数组） 空格/换行区域会被认为是文本节点

6. `parentNode()` 访问父节点

```javascript
document.write(div.parentNode.nodeName);
```

7. `createElement()` 创建元素节点

8. `createTextNode()` 创建文本节点

9. `insertBefore()` 插入节点

```javascript
function insertNode() {
    var div = document.getElementById("divId");
    var node = document.getElementById("pid");
    var newNode = document.createElement("p");
    var textNode = document.createTextNode("fuck");
    newNode.appendChild(textNode);
    div.insertBefore(newNode, node);
}
```

10. `appendChild()` 结尾处添加节点

11. `removeChild()` 删除节点

```javascript
// 将表格1中的节点移动至表格2
function changeNode() {
    var nodes = document.getElementById("ul1");
    var node = nodes.removeChild(nodes.childNodes[7]);
    var list = document.getElementById("ul2");
    list.insertBefore(node, list.childNodes[1]);
}
```

12. `documentElement` `offsetHeight` 网页尺寸

```javascript
var height = document.documentElement.offsetHeight || document.body.offsetHeight;
```
## 事件处理

### 事件流

1. 定义：描述的是页面中接受事件的顺序（比如嵌套的元素都有相同的相应函数时应该先相应哪个）

2. 事件冒泡：有最具体的元素接收，然后逐级向上传播至最不具体的元素节点（文档）

3. 事件捕获：最不具体的节点先接收事件，而最具体的节点应该是最后接收事件

### 事件处理方式

1. html事件处理

```html
<button id="btn" onclick="f()">change img</button>
```

2. DOM0事件处理

```javascript
var btn = document.getElementById("btn");
btn.onclick = function () {
    alert("hello");                 //此处会被覆盖
};
btn.onclick = function () {
    alert("world");
};
```

3. DOM2事件处理

```javascript
btn.addEventListener("click", hello);       //添加事件
btn.addEventListener("click", world);
btn.removeEventListener("click", hello);    //移出事件
function hello() {
    alert("hello");
}
function world() {
    alert("world");
}
```

4. IE事件处理 浏览器兼容性？

```javascript
var btn = document.getElementById("btn");
if(btn.addEventListener){
    btn.addEventListener("click", demo);
}
else if(btn.attachEvent){
    btn.attachEvent("click", demo);
}
else {
    btn.onclick = demo();
}
function demo() {
    alert("hello");
}
```

## 事件对象

定义：触发dom事件的时候都会产生一个对象（`event`）

1. `type` 事件类型

```javascript
document.getElementById("btn").addEventListener("mouseover", showType);
function showType(event) {
    alert(event.type)
    alert(event.target);
}
```

2. `target` 事件目标

3. `stopPropagation()` 阻止事件冒泡

```html
<div id="div">
    <button id="btn">button</button>
</div>
<script>
    document.getElementById("div").addEventListener("click", showType);
    document.getElementById("btn").addEventListener("click", showType);
    function showType(event) {
        alert(event.target);
        event.stopPropagation();
    }
</script>
```

4. `preventDefault()` 阻止默认行为

```javascript
document.getElementById("aid").addEventListener("click", divF);
function divF(event) {
    alert("hello");
    event.stopPropagation();
    event.preventDefault();
}
```

## 对象

### 自定义对象

1. 定义并创建对象实例

```javascript
var man = new Object();
man.name = "hauru";
man.age = 22;
document.write("name:" + man.name + " age:" + man.age);

var man = {name: "hauru", age: 22};
document.write("name:" + man.name + " age:" + man.age);
```

2. 使用函数定义对象，然后创建新的对象实例(常用)

```javascript
function man(name, age) {
    this.name = name;
    this.age = age;
}
var man = new man("hauru", 22);
document.write("name:" + man.name + " age:" + man.age);
```

### String对象

```javascript
var str = "hello Hauru x";
document.write(str.length);
document.write(str.indexOf("Ha"));          //查找子字符串位置 失败返回-1
document.write(str.match("Ha"));            //匹配子字符串 成功则返回子串内容 失败返回null
document.write(str.replace("x", "max"));    //替换 不会改变字符串内容
document.write(str.toUpperCase());          //大小写转化
document.write(str.toLowerCase());
document.write(str.split(" ")[1]);          //分割为数组
```

### Date

```html
<!--页面时钟-->
<body onload="startTime()">
    <div id="timeDiv"></div>
    <script>
        function startTime() {
            var date = new Date();
            var y = date.getFullYear(); //获取年份
            var d = date.getDay();      //获取星期
            var h = date.getHours();
            var m = date.getMinutes();
            var s = date.getSeconds();
            document.getElementById("timeDiv").innerHTML =
                    (y + " " + h + ":" + m + ":" + s);
            setTimeout(startTime, 500);
        }
    </script>
</body>
```

### Math

```javascript
document.write(Math.random());              //随机数
document.write(parseInt(10*Math.random()));
//        max最大值 min最小值 abs绝对值
```

---

## window 对象

window对象指当前的浏览器窗口，所有的js全局对象，函数及变量均自动成为window对象成员

全局变量是window对象的属性

全局函数是window对象的方法 调用之后可直接省略`window`

html DOM的document也是window对象属性之一

### window尺寸

1. `window.innerWidth` 宽

2. `window.innerHeight` 高

### 打开，关闭窗口

```javascript
// 打开窗口
window.open("test2.html", "another", "height=200,width=200,top=100,left=100);
//第二个参数 窗口页标识符，如有相同标识符的窗口存在则不会再次创建

// 关闭窗口 存在浏览器兼容性问题
window.close();
```

### 计时器

1. `setInterval()` 间隔指定毫秒数不停执行指定的代码
 
   `clearInterval()` 停止上述函数的执行的代码
   
```javascript
function startTime() {
    start = setInterval(function () {
        var d = new Date();
//                var t = d.toLocaleDateString() + d.toLocaleTimeString();
        var t = d.toLocaleString();
        document.getElementById("ptime").innerHTML = t;
    }, 500);
}
function clearTime() {
    clearInterval(start);
}
```

2. `setTimeout()` 暂定指定毫秒数后执行指定代码，可递归调用达到反复执行效果

 `clearTimeout()` 停止上述函数的执行的代码
 
### History对象

`window.history` 对象包含浏览器历史的集合

1. `history.back();` 浏览器回退按钮

2. `history.forward()` 浏览器前进按钮

3. `history.go(-1)` 

### location对象

属性与方法

1. `hostname` web主机域名

2. `pathname` 当前页面的路径和文件名

3. `port` 主机端口

4. `protocol` 所使用的web协议（http https）

5. `href` 当前页的url

6. `assign()` 重新加载新的文档

### screen对象

1. `height` 屏幕高度

2. `width` 屏幕宽度

3. `availHeight` 可用的屏幕高度

4. `availWidth` 可用的屏幕宽度