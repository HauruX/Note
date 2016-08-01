# html基础

## HTML头部声明

HTML5 `<!DOCTYPE html>`

HTML4.01 ``

---

## HTML head标签
编码声明 `<meta charset="UTF-8">`

标题 `<title>this is a title</title>`

---

## HTML元素结构

普通标签 `<开始标签 属性="值">元素内容</结束标签>`

空标签 `<br />`

HTML实体可用于显示HTML中的特殊字符

---

## HTML标签与属性

### 通用属性
- class
- id
- style
- title     规定额外信息

### 标签与属性

`<body>`
- `bgcolor` 背景颜色

- `background` 背景图片

`<h1~h6>`
- `align` 对齐方式

`<a>`
- `href` 链接地址
- `target` 规定何处打开链接（`_blank` 新标签页中打开 `_self`默认本页打开 ）
- `name` 页面内连接 `href="#name"`

`<img>`
- `alt` 替代文本（当图片无法显示时）
- `width`
- `height`

### 表格标签

`<table>` 表格

- `border` 表格边界

- `cellpadding` 单元格边距

- `cellspacing` 单元格间距

- `bgcolor` 背景颜色

- `background` 背景图片


`<caption>` 标题

`<tr>` 行

`<th>` 表头

`<td>` 普通单元

- `colspan` 合并单元格数量

### 列表标签

```html
<ol type="a" start="3">
    <li>html</li>
    <li>css</li>
</ol>
<ul type="circle">
    <li>html</li>
    <li>css</li>
</ul>
<dl>
    <dt>html</dt>
        <dd>超文本标记语言</dd>
    <dt>css</dt>
        <dd>层叠样式表</dd>
</dl>
```

`<ol>` 有序列表

- `type` 序号类型 （1 a A i I）

`<ul>` 无序列表

- `type` （`disc`实心圆 `circle`空心圆 `square`方块）

- `start` 起始序号

`<li>` 列表项

`<dl>` 列表

`<dt>` 列表项

`<dd>`  描述

### 格式化标签

`<b>` 粗体

`<em>` 着重

`<i>` 斜体

`<small>` 小号

`<strong>` 加重

`<sub>` 下标

`<sup>` 上标

`<bins>` 插入字

`<del>` 删除字

### HTML块

```html
<div>
    <p><span>this is</span> a test</p>
</div>
```

1. HTML块元素 通常以新行开始 如：`<h1>` `<p>` `<ul>`

2. HTML内联元素 通常不以新行开始 如：`<b>` `<a>` `<img>`

3. `<div>` 块元素 组合HTML元素的容器

4. `<span>` 内联元素 文本的容器

### 表单标签

```html
<form action="" method="GET">
    username:<input type="text" name="username">
    password:<input type="password" name="password">    <br /><br />
    do you like  <!--复选框-->                        <br />
    <input type="checkbox" name="banana" checked>banana       <br />
    <input type="checkbox" name="apple" checked="">apple         <br />
    <input type="checkbox" name="orange" checked=checked>orange       <br />
    <input type="checkbox" name="pair">pair           <br /><br />
    your sex:   <!--单选框-->
    <input type="radio" name="sex" value="man">man
    <input type="radio" name="sex" value="woman">woman      <br /><br />
    your favorite website:  <!--下拉列表-->
    <select name="favorite_website" id="">
        <option value="google">google.com</option>
        <option value="amazon">amazon.com</option>
        <option value="facebook">facebook.com</option>
    </select>                           <br /><br />
    <textarea name="" id="" cols="30" rows="10"></textarea> <br /><br />
    <input type="button" value="button">
    <input type="submit" value="submit">
</form>
```

### 框架标签

```html
<iframe src="frameB.html" frameborder="0" width="400px" height="400px"></iframe>
```
`<a>`
- `target` (`_top`顶层框架打开链接 `_parent`上层框架打开链接)

---

---

## HTML5

### 语法变化
- `DOCTYPE`声明
- 指定字符编码
- 可省略标记的元素
- 具有boolean值的属性
- 可省略属性值的引号

---

### 新增的全局属性

- `contenteditable` 是否可编辑
- `designMode` 
- `hidden` 是否被渲染（隐藏）
- `spellcheck` 是否启用拼写检查
- `tabindex` tab键选中次序

---

### 新增标签

#### 主题结构元素

`<article>` 独立、完整、可独立被外部引用的内容。可以嵌套使用，可标志插件。
是一种特殊的 `<section>` 更强调独立性

```html
<!--页面嵌套-->
<article>
    <header>
        <h2>内嵌页面</h2>
    </header>
    <object data="" type="">
        <embed src="#" type="" width="100" height="100">
    </object>
    <footer>
        <p>foot</p>
    </footer>
</article>
```

`<section>` 用于内容分块，由内容与标题组成。强调分段、分块，要有标题，不要作为设置样式的容器（div的职能）

```html
<!---->
<article>
    <h1>fruit</h1>
    <p>delicious</p>
    <section>
        <h2>apple</h2>
        <p>red</p>
    </section>
    <section>
        <h2>orange</h2>
        <p>yellow</p>
    </section>
</article>
```

`<nav>` 用作页面导航链接组。只放入主要的、基本的链接组。
应用场景：传统导航栏条 侧边导航栏 页内导航栏 翻页操作

```html
<nav>
    <ul>
        <li><a href="#">main page</a></li>
        <li><a href="#">document</a></li>
    </ul>
</nav>
```


`<aside>` 用于表示当前页面或文章的附属信息部分，
包括引用、侧边栏、广告、导航条等区别于主要内容的部分

```html
<article>
    <h1>语法</h1>
    <p>正文</p>
    <aside>
        <h1>名词解释</h1>
        <p>语法：这是一种很重要的内容体</p>
    </aside>
</article>
```

`<time>` 

```html
    <time datetime="2015-10-10T20:00" pubdate="true">2015-10-10 20:00</time>
```

#### 非主题结构元素

`<header>` 具有引导或导航作用的元素，
通常用来放置整个页面或页面内容区块的标题，可包含其他内容如表格、搜索表单、logo

```html
<header>
    <h1>IT</h1>
    <a href="http://google.com">google</a>
    <nav>
        <ul>
            <li><a href="#">page</a></li>
            <li><a href="#">photo</a></li>
            <li><a href="#">video</a></li>
        </ul>
    </nav>
</header>

<article>
    <header>
        <h2>html5</h2>
    </header>
</article>
```

`<footer>` 用作上层腹肌关系内容区块或一个根区块的注脚。
通常包括相关区块的注脚信息，如作者、相关阅读链接、版权信息等

```html
<footer>
    <ul>
        <li><a href="#">版权信息</a></li>
        <li><a href="#">站点地图</a></li>
        <li><a href="#">联系方式</a></li>
    </ul>
</footer>            
<!--</div>-->

<article>
    <footer>
        这是文章的底部
    </footer>
</article>
```

`<hgroup>` 将标题及其子标题进行分组。
通常将h1~h6进行分组，譬如一个内容区块的标题及其子元素算一组

```html
<article>
    <hgroup>
        <h1>标题</h1>
        <h2>子标题</h2>
    </hgroup>
    <p></p>
</article>
```

`<address>` 用于呈现联系信息，包括文档作者/维护者名字、
网站链接、电子邮箱、真实地址、电话号码等。

---

### HTML5 网页编排规则

1. 显示编排内容区域块 
明确使用section等元素创建文档结构，在每个区域快使用标题h*/hgroup

2. 隐式内容区域块

3. 标题分级

4. 不同区域快可以使用相同标题

---

### 新增的表单元素及属性

- `control` 在标签内部放置一个表单元素，并通过该标签的control属性来访问该表单元素

```html
<script>
    function setValue(){
        var label = document.getElementById("label");
        var textbox = label.control;
        textbox.value="123456";
    }
</script>

<form action="">
    <label id="label">
        邮编:
        <input type="text" id="zip" maxlength="6">
        <small>请输入六位数字</small>
    </label>
    <input type="button" value="设置默认值" onclick="setValue()">
</form>
```

`<input>` 

```html
<form action="" id="testform">
    <input type="submit" value="yes1" formaction="a.jsp" formmethod="POST">
    <input type="submit" value="yes1" formaction="b.jsp" formmethod="GET">
    
    <input type="text" formenctype="text/plain">
    <input type="text" formenctype="multipart/form-data">
    <input type="text" formenctype="application/x-www-form-urlencoded">
</form>
<input type="text" form="testform" name="username" autofocus>

<form action="#">
    <input type="text" required="required">
    <input type="submit">
</form>
```

- `form` 表单从属元素指定`form`属性值为表单的`id`，即可将表单外部元素设置从属

- `formaction` 单击不同的按钮不同页面

- `formmethod` 提交方法（`get`/`post`）

- `formenctype` 指定编码方式，（`<form>`中的`enctype`属性）

- `formtarget` 指定表单提交时后在何处打开页面，参见`<a>` `target`属性

- `autofocus` 页面打开时自动获取光标焦点

- `required` 在表单提交时候检查如果元素内容为空，则不允许提交

- `placeholder` 文本框未输入状态时显示的输入提示

```html
邮编：<input type="text" placeholder="至少6位">
```

- `list` `type="text"` 带有自动隐藏的下拉框的文本框
该属性值为某个`<datalist>`的`id`

```html
<input type="text" list="learninglist">
<datalist id="learninglist">
    <option value="html5">html5</option>
    <option value="android">google android</option>
    <option value="css3"></option>
</datalist>
```
- `autocomplete` 文本框控制自动补全的开关
属性值：`on` `off`

- `pattern` 
属性值为正则表达式，表单提交前会进行检查文本框是否符合给定格式

```html
<form action="http://baidu.com">
    <input type="text" pattern="[A-Z]{3}" name="wd" title="Three letter country code">
    <input type="submit" value="submit">
</form>
```

- `selectionDirection` 当用户用鼠标选取文字时，可以获取选取的方向
属性值为`forward` `backward`，没有选取文字时值为`forward`

```html
<script>
    function f(){
        alert(document.getElementById("txt").selectionDirection);
        alert(document.forms[0]['txt'].selectionDirection);
    }
</script>

<form action="">
    <input type="text" name="txt" id="txt">
    <input type="button" value="check" onclick="f()">
</form>
```

- `indeterminate` `checkbox`的“尚未明确是否选取的状态”
```html
<input type="checkbox" indeterminate id="cb">abc
<script>
    var cb = document.getElementById("cb");
    cb.indeterminate = true;
</script>
```
- `height` `width` 用于指定`image`类型的宽高

```html
<form action="">
    <input type="text" name="name">
    <input type="image" src="36.jpeg" alt="huaji" height="20" width="20">
</form>
```

`<labels>` 绑定到表单元素、button、select的纯文本，点击即效果同被绑定的元素

- `for` 被绑定的元素id

```html 
<!--JavaScript表单验证-->
<script>
    function validate(){
        var textName = document.getElementById("text_name");
        var form = document.getElementById("text_form");
        var button = document.getElementById("btnValidate");
        if(textName.value.trim()==""){
            var label = document.createElement("label");
            label.setAttribute("for", "text_name");
            form.insertBefore(label, button);
            label.innerHTML = "input the name";
            // label = textName.labels[1]
            textName.labels[1].setAttribute("style", "font-size:9px; color:red");
        }
    }
</script>

<form action="" id="text_form">
    <label for="text_name">name:</label>
    <input type="text" id="text_name">
    <input type="button" id="btnValidate" value="validate" onclick="validate()">
</form>
```