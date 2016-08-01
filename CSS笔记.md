# CSS

## 相关标签及属性

`<style>` 样式定义

`<link>` 资源引用

`rel="stylesheet"` 外部样式表

`type="text/css"` 引入文档类型

---

## 样式插入方式

- 外部样式表

```html
<link rel="stylesheet" type="text/css" href="css/mystyle.css" />
```
       
- 内部样式表

```html
<style type="text/css">
    body {background-color: red}
</style>
```
 
- 内联样式表

```html
<p style="color:red"></p>
```
---

## 语法
```css
/*类选择器*/
.div_class{
    property: value;
}
/*组合元素*/
div.div_class{
    property: value;
}
/*多类*/
.div_class1.div_class2{
    property: value;
} 

/*属性选择器*/
[title]{
    property: value;
}
[title=te]{
    property: value;
}
/*根据部分属性值选择*/
[title~=te]{
    property: value;
}

/*选择器分组 selector1 selector2样式相同*/
selector1, selector2{
    property: value;
}

/*派生（后代）选择器 定义selectorA中的selectorB样式*/
selectorA selectorB{
    property: value;
}

/*子元素选择器 只能选择某元素子元素*/
h1>strong{
    property: value;
}

/*id选择器*/
/*一个ID只能在文档中使用一次
不能组合使用
使用JavaScript时需用到ID*/
#div_id{
    property: value;
}

/*相邻兄弟选择器*/
h1+p{
    property: value;
}
```

---

## 基本样式

### 背景

- `background-color` 元素的背景颜色

- `background-image` 元素的背景图片

    ```css
    background-image: url("../img/03.jpg");
    ```

- `background-position` 背景图片的起始位置

    ```css
    /* center left right top bottom */
    background-position: right top;
    background-position: 10px 10px;
    ```

- `background-repeat` 背景图片是否重复

    `no-repeat`不重复 `repeat-x` `repeat-y`仅在横向/纵向重复 `repeat`重复（默认）

- `background-attachment` 背景图片是否固定或随着页面滚动
    ```css
    background-attachment: fixed;
    ```
    
- `background-size` 背景图片尺寸
    
    ```css
    background-size: 100%;
    background-size: 100px 100px;
    ```

- `background-origin` 背景图片定位区域

- `background-clip` 背景绘制区域

### 文本

- `color` 文本颜色

- `text-indent` 缩进元素中的文本首行 常以`em`字符为单位

- `text-align` 对齐元素中的文本

    `center` `right`
    
- `text-transform`  元素中的字母

    `capitalize`首字母大写
    `lowercase`全部小写
    `uppercase`全部大写

- `line-height` 行高

- `letter-spacing` 字符间距

- `direction` 文本方向 

- `text-decoration` 向文本添加注释

- `unicode-bidi` 设置文本方向

- `white-space` 元素中空白的处理方式

- `word-spacing` 字间距

- `text-shadow` 文本添加阴影

    ```css
    /* 横向偏移 纵向偏移 模糊程度 颜色 */
    text-shadow: 5px 5px 1px aqua;
    ```
- `word-wrap` 规定文本换行规则

    ```css
    width: 90px;
    word-wrap: normal;
    ```
    
- `text-overflow: ellipsis` 文本溢出时显示省略号
    
### 字体

- `font-family` 字体系列

    ```css
    /*自定义字体*/
    @font-face{
        font-family: myfont;
        src: url();
    }
    ```

- `font-size` 字体尺寸 单位`px`

- `font-weight` 字体粗细 无单位

- `font-style` 字体风格

- `font-variant` 以小型大写字体或正常字体显示文本

### 链接

    链接的四种状态

    `a:link` 未被访问的链接
    `a:visited` 已经访问的链接
    `a:hover` 鼠标指针位于链接上方
    `a:active` 链接被点击的时刻

- `color` 文本颜色

- `text-decoration` 链接样式，多用于清除下划线
    ```css
    text-decoration: none;
    ```

- `background-color` 背景颜色

### 列表

`<ul>` `<ol>`

- `list-style` 列表属性

    按照顺序分别设置`list-style-type` `list-style-position` `list-style-image` 

`<li>` 

- `list-style-type` 列表项标记的类型

    与`<ul>`中的`type`属性相通（`disc`实心圆 `circle`空心圆 `square`方块　`none`无）

- `list-style-image` 列表项图片

    ```css
    list-style-image: url("../img/03.jpg");
    ```

- `list-style-position` 列表标志位置，属性值`inside` `outside`

### 表格

```html
<table id="tb">
    <tr>
        <th>name</th>
        <th>sex</th>
        <th>age</th>
    </tr>
    <tr>
        <td>hauru</td>
        <td>man</td>
        <td>22</td>
    </tr>
    <tr class="alt">
        <td>hauru</td>
        <td>man</td>
        <td>22</td>
    </tr>
</table>
```
```css
#tb{
    border-collapse: collapse;
    width: 500px;
}
#tb th, #tb td{
    border: 1px solid cornflowerblue;
    padding: 5px;
}
#tb th{
    background-color: aqua;
    text-align: right;
    color: #FFFFFF;
}
#tb tr.alt td{
    background-color: aqua;
    color: black;
}
```

- `border` 表格边框
    ```css
    table, th, td{
        border: 1px solid blue;
    }
    ```
    ```html
    <table border="1px"></table>
    ```
    
- `border-collapse` 折叠边框,将单元格边框与表格外边框合一

    ```css
    table{
        border-collapse: collapse;
    }
    ```

- `width` `height` 宽高

- `text-align` 文本对齐

- `color` 文本颜色

- `background-color` 背景颜色

- `padding` 内编剧

### 轮廓

- `outline` 轮廓属性

- `outline-color` 轮廓颜色

- `outline-style` 轮廓样式

    `groove`实线 `double`双实线 `dotted`虚线

- `outline-width` 轮廓宽度

### 定位

- `position` 

    `static` 静态 `relative` 相对 `absolute` 绝对 `fixed` 固定

- `top` 元素向上偏移量 `static`时无效果 元素原来位置被占据

- `left` 

- `right`

- `bottom`

- `overflow` 元素溢出其区域发生的事情

- `clip` 元素显示的形状

- `vertical-align` 元素垂直对齐方式

- `z-index` 元素堆叠顺序 `static`时无效果

### 浮动

- `float` 浮动

    `left` `right` `none` `inherit`从父级继承浮动属性

- `clear` 去掉浮动属性

    `left` `right` `both` `inherit`
    
### 盒模式

    组成部分：margin border padding content
    
- `padding` 边距

- `padding-top` `padding-bottom` `padding-left` `padding-right`

- `border` 边框

    ```css
    border: 1px solid blue;
    ```

- `border-width` 边框宽度
    
- `border-top-width`

- `border-style` 边框样式

    `groove`实线 `double`双实线 `dotted`虚线

- `border-top-style`

- `border-color` 边框颜色

- `border-top-color` 

---

#### css3新增部分

- `border-radius` 圆角边框，属性值代表圆角程度

    ```css
    p{
        border-radius: 11px;
        width: 100px;
        height: 50px;
        background-color: antiquewhite;
        
        border:　2px solid;
    }
    ```

- `box-shadow` 边框阴影

    ```css
    /* 横向偏移 纵向偏移 模糊程度 颜色 */
    box-shadow: 10px 10px 5px aqua;
    ```

- `border-image` 边框图片

---

- `margin` 外边距宽度，当上下块内容相邻时，存在外边距合并的情况

    ```css
    内容居中
    width: 500px;
    margin: auto;
    /*magin:　0px auto
    上下为0 左右为自动*/
    ```

- `margin-top`

### 对齐操作

- `margin`

- `position` 选择相对布局

- `float`

### 尺寸

- `width` 宽

- `height` 高

- `line-height` 行高，默认值`1`(`normal` `100%`)

- `max-width` 最大宽度

- `min-width` 最小宽度

- `max-height`

- `min-height` 
 
 ### 分类
 
 - `clear`
 
 - `float`;
 
 - `position`
 
 - `cursor` 指向元素之上时显示的指针类型
 
 - `display` 如何显示元素
 
    `none` 不显示，不占据空间
    
    `inline` 显示为内联元素，前后没有换行符
    
    `block`  显示为块级元素，前后有换行符
 
 - `visibility` 是否可见 
    
    ```css
    /*隐藏元素 元素仍占据空间*/
    visibility: hidden;
    ```

### 导航栏

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>text</title>
        <link rel="stylesheet" href="css/navigate.css">
    </head>
    <body>
        <ul>
            <li><a href="#">navigate1</a></li>
            <li><a href="#">navigate2</a></li>
            <li><a href="#">navigate3</a></li>
            <li><a href="#">navigate4</a></li>
        </ul>
    </body>
</html>
```

```css
/*纵向*/
*{
    margin: 0px;
    padding: 0px;
}
ul{
    list-style-type: none;
}

a{
    text-decoration: none;
    color: white;
    background-color: darksalmon;
    display: block;
    width: 80px;
    text-align: center;
}
a:hover{
    background-color: darkgoldenrod;
}
```

```css
/*横向*/
*{
    margin: 0px;
    padding: 0px;
}
ul{
    list-style-type: none;
    background-color: darksalmon;
    width: 380px;
    text-align: center;
}
li{
    display: inline;
    padding: 3px;
    padding-left: 5px;
    padding-right: 5px;
}
a{
    text-decoration: none;
    color: white;
    background-color: darksalmon;
    /*display: block;*/
    width: 80px;
    text-align: center;
    font-weight: bold;
}
a:hover{
    background-color: darkgoldenrod;
}
```

### 瀑布流图片

```html
<div class="container">
    <div class="image">
        <a href="#">
            <img src="img/girl.jpg" alt="girl">
        </a>
        <div class="text">a girl</div>
    </div>
</div>
```

```css
.container{
    width: 70%;
    margin: 10px auto;
}
.image{
    margin: 5px;
    border: 1px solid black;
    /*padding: 2px;*/
    /*width: 200px;*/
    width: auto;
    float: left;
    
    opacity: 1;
}
.image a:hover{
    background-color: darkgray;
}
.image img{
    width: 200px;
    margin: 5px;
}
.image .text{
    text-align: center;
    font-size: 12px;
    margin-bottom: 5px;
}
```

### 2D 3D转换

- `transform`

    ```css
    /*-webkit-transform:  safari chrome
    -ms-transform:  IE
    -o-transform:  opera
    -moz-transform:  firefox*/
    
    /*2D*/
    /*平移*/
    transform: translate(200px, 100px); 
    /*旋转20度*/
    transform: rotate(20deg);
    /*缩放*/
    transform: scale(1, 2);
    /*倾斜*/
    transform: skew(20deg);
    transform: matrix();
    
    /*3D*/
    transform: rotateX(10deg);
    transform: rotateY(10deg);
    ```
    
### 过渡

```css
div{
    width: 100px;
    height: 100px;
    background-color: blueviolet;
    /*-webkit-transition: width 2s, height 2s, -webkit-transform 2s;*/
    transition: width 1s, height 2s, transform 1s;
}
div:hover{
    width: 200px;
    height: 200px;
    transform: rotate(360deg);
    /*-webkit-transform: rotate(360deg);*/
}
```

- `transition` 设置四个过渡属性

- `transition-property` 过渡的名称

- `transition-duration` 过渡效果花费的时间

- `transition-timing-function` 过渡效果的时间曲线 

- `transition-delay` 过渡效果开始时间

### 动画

遵循`@keyframes`规则，规定动画时常、名称
    
```css
div{
    width: 100px;
    height: 100px;
    position: relative;
    animation: anim 5s;
    /*-webkit-animation: */
}
@keyframes anim{
    0%{background-color: red; left: 0px; top: 0px;}
    25%{background-color: aqua; left: 200px; top: 0px;}
    50%{background-color: blueviolet; left: 200px; top: 200px;}
    75%{background-color: coral; left: 0px; top: 200px;}
    100%{background-color: red; left: 0px; top: 0px;}
}
/*@-webkit-keyframes anim{}*/
```

### 多列

```css
.div1{
    column-count: 3;
    column-gap: 50px;
    column-rule: 2px outset red;
    -webkit-column-count: 3;
    -webkit-column-gap: 50px;
    -webkit-column-rule: 2px outset red;
}
```

```html
/*多列瀑布流图片*/
<div class="container">
        <div><img src="img/1.jpg" alt=""></div>
        <div><img src="img/2.jpg" alt=""></div>
    </div>
```
```css
.container{
    /*column-count: */
    column-width: 250px;
    column-gap: 5px;
    -webkit-column-width: 250px;
    -webkit-column-gap: 5px;
}
.container div{
    width: 250px;
    margin: 5px 0;    
}
.container img{
    width: 250px;
}
```

- `column-count` 分列数量

- `column-width` 列宽

- `column-gap` 列间距

- `column-rule` 分隔栏属性
