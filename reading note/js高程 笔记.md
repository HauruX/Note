### 5.2.5

排序算法 Array.short()

调用每个数组项的`toString()`进行转化，对转化结果进行比较

```javascript
([0, 1, 10, 15, 5]).sort()
//output : [0, 1, 10, 15, 5]
```

解决方法：自己定义一个`compare`函数，在调用`sort()`时候传入

```javascript
([0, 1, 10, 15, 5]).sort(function(value1, value2){
    if(value1 < value2){
        return -1;
    }
    else if(value1 > value2){
        return 1;
    }
    else{
        return 0;
    }
})

([0, 1, 10, 15, 5]).sort(function(value1, value2){
    return (value1 - value2)
})
```

### 6.2.3

in
可用于判断属性是否属于某个对象，包括自己的属性、原型链继承的属性、隐藏属性
for-in
只列举可枚举的属性，包括自己属性、原型链继承的属性

# 7

函数声明的两种方式
普通声明 functiong functionName(){}
函数表达式 var functionName = functiong(){}

函数存在声明提前情况



# 10章 dom

## 10.1 节点层次

### 10.1.1 Node类型

DOM1定义Node接口，该接口在javascript中作为Node类型实现，除ie外所有浏览器均可访问到该类型。所有节点类型都继承自该类型

文档节点是`document`，只有一个子节点；文档元素是文档的最外层节点，html中是`<html>`元素

#### 部分属性

`nodeType` 属性

- 1 Node.ELEMENT_NODE
- 2 Node.ATTRIBUTE_NODE
- 3 Node.TEXT_NODE
...

ie没有公开Node构造函数，为了兼容ie，建议使用数字与nodeType作比较

```javascript
if(someNode.nodeType === 1){
    console.log("this node is ELEMENT_NODE");
}
```

`nodeName` 属性 ： 元素节点中是元素标签名（大写，如"DIV"）

`nodeValue` 属性 ： 始终为null

#### 节点关系

节点关系可通过家族关系描述，子元素、父元素、同胞元素

`childNodes` 属性

值是`NodeList`对象，是动态结构，dom改变时，该对象随之改变。类数组，和`arguments`对象一样可以使用`Array.prototype.slice()`方法转换为数组（ie8及更早版本需要手动枚举方式转换）

```javascript
someNode.childNodes[0];         // 第一个子元素
someNode.childNodes.item(0);
someNode.childNodes.length;     // 子元素数量
```

`firstChild` 第一个子节点 相当于`someNode.childNodes[0]` `previousSibling`为null

`lastChild` 最后一个子节点 相当于`someNode.childNodes[someNode.childNodes.length-1]` `nextSibling`为null

`hasChildNodes` 是否有子节点，相当于`someNode.childNodes.length !== 0`

`parentNode` 父节点

`previousSibling` 前一个节点

`nextSibling` 后一个节点

`ownerDocument` 指向整个文档的文档节点

#### 节点操作

`appendChild` 在子元素列表末尾插入新元素(`lastChild`)，参数为要插入的节点，返回值为插入的节点;如果传入的新元素已经存在于文档中，则该节点从原来位置移动到新位置，dom节点不能同时出现在文档的多个位置

`insertBefore` 参数为要插入的节点、参考位置节点（如果为null，则与`appendChild`相同）；需要通过父节点调用

`replaceChild` 参数为要插入的节点、被替换的节点，返回值为被替换的节点；被替换的节点仍存在于文档中，但是没有位置；需要通过父节点调用

`removeChild` 参数为要移除的节点，返回值为被移除的节点；被替换的节点仍存在于文档中，但是没有位置；需要通过父节点调用

`cloneNode` 复制克隆节点，参数为是否深复制，如果为`true`则深复制该节点以及节点树，为空或`false`则只复制该标签，返回值为复制产生的结果；该方法不会复制添加到dom节点中的js属性

`normalize` 仅针对文本节点，删除空文本节点，合并相邻文本节点





11.3 dom html5扩充

`getElementsByClassName`

`classList` 方法 `add` `remove` `contains` `toggle`