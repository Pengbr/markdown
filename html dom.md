# HTML DOM 教程

DOM (Document Object Model) 译为**文档对象模型**，是 HTML 和 XML 文档的编程接口。

HTML DOM 定义了访问和操作 HTML 文档的标准方法。

DOM 以树结构表达 HTML 文档。

## HTML DOM 树形结构:

![DOM HTML tree](https://www.runoob.com/images/htmltree.gif)

# HTML DOM 简介

HTML DOM 定义了访问和操作 HTML 文档的标准。

*HTML DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。*

**dom即增删改查。**

# HTML DOM 节点

在 HTML DOM 中，所有事物都是节点。DOM 是被视为节点树的 HTML。

## DOM 节点

根据 W3C 的 HTML DOM 标准，HTML 文档中的所有内容都是节点：

- 整个文档是一个文档节点
- 每个 HTML 元素是元素节点
- HTML 元素内的文本是文本节点
- 每个 HTML 属性是属性节点
- 注释是注释节点

## 节点父、子和同胞

节点树中的节点彼此拥有层级关系。

我们常用**父（parent）**、**子（child）**和**同胞（sibling）**等术语来描述这些关系。父节点拥有子节点。同级的子节点被称为同胞（兄弟或姐妹）。

- 在节点树中，顶端节点被称为根（root）。
- 每个节点都有父节点、除了根（它没有父节点）。
- 一个节点可拥有任意数量的子节点。
- 同胞是拥有相同父节点的节点。

下面的图片展示了节点树的一部分，以及节点之间的关系：

![Node tree](https://www.runoob.com/wp-content/uploads/2013/09/dom_navigate.gif)

# HTML DOM 方法

HTML DOM 方法是我们可以在节点（HTML 元素）上执行的动作。

HTML DOM 属性是我们可以在节点（HTML 元素）设置和修改的值。

## 一些 DOM 对象方法

|           方法           |                             描述                             |
| :----------------------: | :----------------------------------------------------------: |
|     getElementById()     |                   返回带有指定 ID 的元素。                   |
|  getElementsByTagName()  | 返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。 |
| getElementsByClassName() |          返回包含带有指定类名的所有元素的节点列表。          |
|      appendChild()       |                 把新的子节点添加到指定节点。                 |
|      removeChild()       |                         删除子节点。                         |
|      replaceChild()      |                         替换子节点。                         |
|      insertBefore()      |              在指定的子节点前面插入新的子节点。              |
|    createAttribute()     |                        创建属性节点。                        |
|     createElement()      |                        创建元素节点。                        |
|     createTextNode()     |                        创建文本节点。                        |
|      getAttribute()      |                      返回指定的属性值。                      |
|      setAttribute()      |               把指定属性设置或修改为指定的值。               |

# HTML DOM 属性

## innerHTML 属性

获取元素内容的最简单方法是使用 innerHTML 属性。

innerHTML 属性对于获取或替换 HTML 元素的内容很有用。

## nodeValue 属性

nodeValue 属性规定节点的值。

- 元素节点的 nodeValue 是 undefined 或 null
- 文本节点的 nodeValue 是文本本身
- 属性节点的 nodeValue 是属性值

## nodeType 属性

nodeType 属性返回节点的类型。nodeType 是只读的。

比较重要的节点类型有：

| 元素类型 | NodeType |
| :------: | :------: |
|   元素   |    1     |
|   属性   |    2     |
|   文本   |    3     |
|   注释   |    8     |
|   文档   |    9     |

# HTML DOM 访问

## 访问 HTML 元素（节点）

访问 HTML 元素等同于访问节点

您能够以不同的方式来访问 HTML 元素：

- 通过使用 getElementById() 方法
- 通过使用 getElementsByTagName() 方法
- 通过使用 getElementsByClassName() 方法

# HTML DOM - 修改

## 改变 HTML 样式

```html
<p id="p1">Hello world!</p>
<p id="p2">Hello world!</p>
 
<script>
document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
</script>
```

## 创建新的 HTML 元素

如需向 HTML DOM 添加新元素，您首先必须创建该元素（元素节点），然后把它追加到已有的元素上。

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另一个段落。</p>
</div>
<script>
var para=document.createElement("p");
var node=document.createTextNode("这是一个新段落。");
para.appendChild(node);
var element=document.getElementById("div1");
element.appendChild(para);
</script>
```

# HTML DOM - 元素

## 创建新的 HTML 元素 - insertBefore()

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var para=document.createElement("p");
var node=document.createTextNode("这是一个新段落。");
para.appendChild(node);
 
var element=document.getElementById("div1");
var child=document.getElementById("p1");
element.insertBefore(para,child);
</script>
```

## 删除已有的 HTML 元素

如需删除 HTML 元素，您必须清楚该元素的父元素：

**有几个方法必须先找到父节点**

```html
<div id="div1">
    <p id="p1">这是一个段落。</p>
    <p id="p2">这是另一个段落。</p>
</div>
<script>
var parent=document.getElementById("div1");
var child=document.getElementById("p1");
parent.removeChild(child);
</script>
```

找到您需要删除的子元素，然后使用 parentNode 属性来查找其父元素：

```js
var child=document.getElementById("p1");
child.parentNode.removeChild(child);
```

## 替换 HTML 元素

如需替换 HTML DOM 中的元素，请使用 replaceChild() 方法：

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
 
<script>
var parent=document.getElementById("div1");
var child=document.getElementById("p1");
var para=document.createElement("p");
var node=document.createTextNode("这是一个新的段落。");
para.appendChild(node);
parent.replaceChild(para,child);
</script>
```

# HTML DOM - 事件

```js
onclick=JavaScript
```

# HTML DOM 导航

## 导航节点关系

您能够使用三个节点属性：parentNode、firstChild 以及 lastChild ，在文档结构中进行导航。

请看下面的 HTML 片段：

```html
<html>
<head>
<meta charset="utf-8">
</head>
<body>
 
<p>Hello World!</p>
<div>
  <p>DOM 是非常有用的!</p>
  <p>这个实例演示了节点的关系。</p>
</div>
 
</body>
</html>
```

- 首个 <p> 元素是 <body> 元素的首个子元素（firstChild）
- <div> 元素是 <body> 元素的最后一个子元素（lastChild）
- <body> 元素是首个 <p> 元素和 <div> 元素的父节点（parentNode）

## DOM 根节点

这里有两个特殊的属性，可以访问全部文档：

- document.documentElement - 全部文档
- document.body - 文档的主体

```html
<p>Hello World!</p>
<div>
    <p>DOM 是非常有用的!</p>
    <p>这个实例演示了 <b>document.body</b> 属性。</p>
</div>
 
<script>
alert(document.body.innerHTML);
</script>
```

## childNodes 和 nodeValue

除了 innerHTML 属性，您也可以使用 childNodes 和 nodeValue 属性来获取元素的内容。

下面的代码获取 id="intro" 的 <p> 元素的值：

```html
<p id="intro">Hello World!</p>
 
<script>
txt=document.getElementById("intro").childNodes[0].nodeValue;
document.write(txt);
</script>
```

