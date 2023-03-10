# CSS 教程

## CSS 实例



```css
body {    
	background-color:#d0e4fe; } 

h1 {    
	color:orange;   
    text-align:center; } 

p {    
	font-family:"Times New Roman";   
	font-size:20px; }
```



# CSS 简介

# CSS 语法

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明:

![img](https://www.runoob.com/wp-content/uploads/2013/07/632877C9-2462-41D6-BD0E-F7317E4C42AC.jpg)

CSS声明总是以分号(;)结束，声明总以大括号({})括起来:

```css
p {    color:red;    text-align:center; }
```

CSS注释以 **/\*** 开始, 以 ***/** 结束

# CSS Id 和 Class

HTML元素以id属性来设置id选择器,CSS 中 id 选择器以 "#" 来定义。

ID属性不要以数字开头，数字开头的ID在 Mozilla/Firefox 浏览器中不起作用。

```css
#para1
{
    text-align:center;
    color:red;
}

```

class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在**多个元素**中使用。

class 选择器在HTML中以class属性表示, 在 CSS 中，类选择器以一个点"."号显示

```css
.center {text-align:center;}
```

# CSS 创建

插入样式表的方法有三种:

- 外部样式表(External style sheet)
- 内部样式表(Internal style sheet)
- 内联样式(Inline style)

## 外部样式表

<head> 
    <link rel="stylesheet" type="text/css" 		href="mystyle.css"> 
</head>

## 内部样式表

<head> 
<style> 
    hr {color:sienna;} 
    p {margin-left:20px;} 
    body {background-image:url("images/back40.gif");} 
</style> 
</head>

## 内联样式

<p style="color:sienna;margin-left:20px">这是一个段落。</p>

## 多重样式

如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 

# CSS 背景

background-image 属性描述了元素的背景图像.

默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体.

页面背景图片设置实例:

```css
body {background-image:url('paper.gif');}
```

让背景图像不影响文本的排版

如果你不想让图像平铺，你可以使用 background-repeat 属性:

```css
body
{
background-image:url('img_tree.png');
background-repeat:no-repeat;
}
```

平铺：就是把图片铺满桌面，因为一张图片可能不能占满整个桌面，就用几张图片铺满桌面。

拉伸：就是把图片放大，让一张图片就占满桌面。

居中：把图片放在桌面中间。

# CSS 文本格式

## 文本修饰

text-decoration 属性用来设置或删除文本的装饰。

从设计的角度看 text-decoration属性主要是用来删除链接的下划线：

```css
a {text-decoration:none;}
```

也可以这样装饰文字：

```css
h1 {text-decoration:overline;}
h2 {text-decoration:line-through;}
h3 {text-decoration:underline;}
```

## 文本的对齐方式

```css
h1 {text-align:center;}
p.date {text-align:right;}
```

## 文本转换

```css
p.uppercase {text-transform:uppercase;}
p.lowercase {text-transform:lowercase;}
p.capitalize {text-transform:capitalize;}
```

## 文本缩进

```css
p {text-indent:50px;}
```

# CSS 字体

## 字体系列

font-family 属性设置文本的字体系列。

```css
p{font-family:"Times New Roman", Times, serif;}
```

## 字体样式

```css
p.normal {font-style:normal;}
p.italic {font-style:italic;}
p.oblique {font-style:oblique;}
```

## 字体大小

font-size 属性设置文本的大小。

```css
h1 {font-size:40px;}
h2 {font-size:30px;}
p {font-size:14px;}
```

## 用em来设置字体大小

1em和当前字体大小相等。在浏览器中默认的文字大小是16px。

## 使用百分比和EM组合

```css
body {font-size:100%;}
h1 {font-size:2.5em;}
h2 {font-size:1.875em;}
p {font-size:0.875em;}
```

# CSS 链接

## 链接样式

- a:link - 正常，未访问过的链接
- a:visited - 用户已访问过的链接
- a:hover - 当用户鼠标放在链接上时
- a:active - 链接被点击的那一刻

# CSS 列表

## 移除默认设置

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

# CSS 表格

## 表格边框

```css
table, th, td
{
    border: 1px solid black;
}
```

## 表格宽度和高度

```css
table 
{
    width:100%;
}
th
{
    height:50px;
}
```

## 表格文字对齐

```css
td
{
    text-align:right;
}
td
{
    height:50px;
    vertical-align:bottom;
}
```

## 表格颜色

```css
table, td, th
{
    border:1px solid green;
}
th
{
    background-color:green;
    color:white;
}
```

## 表格格式

![image-20210220231841412](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210220231841412.png)

# CSS 盒子模型

![CSS box-model](https://www.runoob.com/images/box-model.gif)

最终元素的总宽度计算公式是这样的：

总元素的宽度=宽度+左填充+右填充+左边框+右边框+左边距+右边距

元素的总高度最终计算公式是这样的：

总元素的高度=高度+顶部填充+底部填充+上边框+下边框+上边距+下边距

# CSS 边框

## 边框样式

**border-style**属性用来定义边框的样式

![image-20210222223033516](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210222223033516.png)

## 边框宽度

您可以通过 border-width 属性为边框指定宽度。

## 边框颜色

border-color属性用于设置边框的颜色。

## 边框-简写属性

```css
border:5px solid red;
```

# CSS 轮廓（outline）

![Outline](https://www.runoob.com/images/box_outline.gif)

```css
p 
{
	border:1px solid red;
	outline:green dotted thick;
}
```

# CSS margin(外边距)

# CSS padding（填充）

# CSS 分组 和 嵌套 选择器

## 分组选择器

```css
h1,h2,p
{
    color:green;
}
```

## 嵌套选择器

```css
p
{
    color:blue;
    text-align:center;
}
.marked
{
    background-color:red;
}
.marked p
{
    color:white;
}
p.marked{
    text-decoration:underline;
}
```

# CSS 尺寸 (Dimension)

设置行高line-height可以将元素垂直居中

# CSS Display(显示) 与 Visibility（可见性）

display属性设置一个元素应如何显示，visibility属性指定一个元素应可见还是隐藏。

## 隐藏元素 - display:none或visibility:hidden

隐藏一个元素可以通过把display属性设置为"none"，或把visibility属性设置为"hidden"。但是请注意，这两种方法会产生不同的结果。

visibility:hidden可以隐藏某个元素，但隐藏的元素仍需占用与未隐藏之前一样的空间。也就是说，该元素虽然被隐藏了，但仍然会影响布局。

display:none可以隐藏某个元素，且隐藏的元素不会占用任何空间。也就是说，该元素不但被隐藏了，而且该元素原本占用的空间也会从页面布局中消失。

# CSS Position(定位)

## static 定位

HTML 元素的默认值，即没有定位，遵循正常的文档流对象。

静态定位的元素不会受到 top, bottom, left, right影响。

## fixed 定位

元素的位置相对于浏览器窗口是固定位置。

即使窗口是滚动的它也不会移动：

## relative 定位

相对定位元素的定位是相对其正常位置。

## absolute 定位

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>:

**子绝父相**

## sticky 定位

## 重叠的元素

元素的定位与文档流无关，所以它们可以覆盖页面上的其它元素

z-index属性指定了一个元素的堆叠顺序（哪个元素应该放在前面，或后面）

一个元素可以有正数或负数的堆叠顺序：

```css
img
{
    position:absolute;
    left:0px;
    top:0px;
    z-index:-1;
}
```

具有更高堆叠顺序的元素总是在较低的堆叠顺序元素的前面。

**注意：** 如果两个定位元素重叠，没有指定z - index，最后定位在HTML代码中的元素将被显示在最前面。

# CSS 布局 - Overflow

| 值      |                           描述                           |
| :------ | :------------------------------------------------------: |
| visible |       默认值。内容不会被修剪，会呈现在元素框之外。       |
| hidden  |          内容会被修剪，并且其余内容是不可见的。          |
| scroll  | 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。 |
| auto    | 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。 |
| inherit |         规定应该从父元素继承 overflow 属性的值。         |

# CSS Float(浮动)

## 清除浮动 - 使用 clear

元素浮动之后，周围的元素会重新排列，为了避免这种情况，使用 clear 属性。

clear 属性指定元素两侧不能出现浮动元素。

```css
.box
{
    clear:both;
}
```

# CSS 布局 - 水平 & 垂直对齐

*注意：如果子元素的高度大于父元素，且子元素设置了浮动，那么子元素将溢出，这时候你可以使用 "***clearfix***(清除浮动)" 来解决该问题。*

.clearfix类避免高度塌陷和垂直外边距重叠。	

# CSS 组合选择符

在 CSS3 中包含了四种组合方式:

- 后代选择器(以空格   分隔)
- 子元素选择器(以大于 **>** 号分隔）
- 相邻兄弟选择器（以加号 **+** 分隔）
- 普通兄弟选择器（以波浪号 **～** 分隔）

## 后代选择器

```css
div p
{
  background-color:yellow;
}
```

## 子元素选择器

```css
div>p
{
  background-color:yellow;
}
```

## 相邻兄弟选择器

```css
div+p
{
  background-color:yellow;
}
```

## 后续兄弟选择器

```css
div~p
{
  background-color:yellow;
}
```

# CSS 伪类(Pseudo-classes)

## anchor伪类

```css
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

## CSS :first-child 伪类

```css
p:first-child
{
    color:blue;
}
```

# CSS 伪元素

## :first-line 伪元素

"first-line" 伪元素用于向文本的首行设置特殊样式。

```css
p:first-line 
{
    color:#ff0000;
    font-variant:small-caps;
}
```

## :first-letter 伪元素

```css
p:first-letter 
{
    color:#ff0000;
    font-size:xx-large;
}
```

## CSS - :before 伪元素

":before" 伪元素可以在元素的内容前面插入新内容。

```css
h1:before 
{
    content:url(smiley.gif);
}
```

## CSS - :after 伪元素

":after" 伪元素可以在元素的内容之后插入新内容。

```css
h1:after
{
    content:url(smiley.gif);
}
```

**伪类选择元素基于的是当前元素处于的状态，或者说元素当前所具有的特性，而不是元素的id、class、属性等静态的标志。由于状态是动态变化的，所以一个元素达到一个特定状态时，它可能得到一个伪类的样式；当状态改变时，它又会失去这个样式。由此可以看出，它的功能和class有些类似，但它是基于文档之外的抽象，所以叫伪类。**

**与伪类针对特殊状态的元素不同的是，**伪元素**是对元素中的特定内容进行操作，它所操作的层次比伪类更深了一层，也因此它的动态性比伪类要低得多。实际上，设计伪元素的目的就是去选取诸如元素内容第一个字（母）、第一行，选取某些内容前面或后面这种普通的选择器无法完成的工作。它控制的内容实际上和元素是相同的，但是它本身只是基于元素的抽象，并不存在于文档中，所以叫伪元素。**

# CSS 导航栏

## 导航栏=链接列表

导航条基本上是一个链接列表，所以使用 <ul> 和 <li>元素非常有意义

# CSS 下拉菜单

## 基本下拉菜单

```css
<style>
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  padding: 12px 16px;
}
.dropdown:hover .dropdown-content {
  display: block;
}
</style>
[mycode3]
[mycode3 type="html"]
<div class="dropdown">
  <span>鼠标移动到我这！</span>
  <div class="dropdown-content">
    <p>菜鸟教程</p>
    <p>www.runoob.com</p>
  </div>
</div>
```

**注意**：需要设置下拉框的内容开启相对定位，下拉框开启绝对定位，下拉框是需要下拉内容的子元素。

# CSS 图像透明/不透明

CSS3中属性的透明度是 **opacity**。

# CSS 属性 选择器

## 具有特定属性的HTML元素样式

具有特定属性的HTML元素样式不仅仅是class和id。

```css
[title]
{
    color:blue;
}


[title=runoob]
{
    border:5px solid green;
}
```

# CSS 表单

- `input[type=text]` - 选取文本输入框
- `input[type=password]` - 选择密码的输入框
- `input[type=number]` - 选择数字的输入框

## 输入框(input) 聚焦

```css
input[type=text]:focus {
  background-color: lightblue;
}
```

## 下拉菜单（select）样式

```css
select {
  width: 100%;
  padding: 16px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;
}
```

# CSS content 属性

```css
a:after
{
    content: " (" attr(href) ")";
}
```

# CSS 网页布局

![img](https://www.runoob.com/wp-content/uploads/2019/04/DBD1E737-47C5-445E-BFEC-7547210D88D5.jpg)

# CSS3 教程

# CSS3 边框

## CSS3 圆角

```css
div
{
border:2px solid;
border-radius:25px;
}
```

## CSS3 盒阴影

```css
div
{
box-shadow: 10px 10px 5px #888888;
}
```

# CSS3 背景

## CSS3 的 background-origin 属性

background-origin 属性指定了背景图像的位置区域。

content-box, padding-box,和 border-box区域内可以放置背景图像。

![img](https://www.runoob.com/images/background-origin.gif)

```css
div
{
    background:url(img_flwr.gif);
    background-repeat:no-repeat;
    background-size:100% 100%;
    background-origin:content-box;
}
```

## CSS3 background-clip属性

CSS3中background-clip背景剪裁属性是从指定位置开始绘制。

```css
#example1 { 
    border: 10px dotted black; 
    padding: 35px; 
    background: yellow; 
    background-clip: content-box; 
}
```

# CSS3 渐变（Gradients）

- **线性渐变（Linear Gradients）- 向下/向上/向左/向右/对角方向**
- **径向渐变（Radial Gradients）- 由它们的中心定义**

角度是指水平线和渐变线之间的角度，逆时针方向计算。换句话说，0deg 将创建一个从下到上的渐变，90deg 将创建一个从左到右的渐变。

![img](https://www.runoob.com/wp-content/uploads/2014/07/7B0CC41A-86DC-4E1B-8A69-A410E6764B91.jpg)

# CSS3 文本效果

在css中，white-space属性是用来定义元素内的空白该如何处理。

white-space属性值

normal：忽略多余的空白，只保留一个空白（默认）；
pre：保留空白(行为方式类似于html中的pre标签)；
nowrap：只保留一个空白，文本不会换行，会在在同一行上继续，直到遇到br标签为止。
pre-wrap：保留空白符序列，正常地进行换行；
pre-line：合并空白符序列，保留换行符；
inherit：从父元素继承white-space属性的值。

# CSS3 字体

```css
<style> 
@font-face
{
    font-family: myFirstFont;
    src: url(sansation_light.woff);
}
 
div
{
    font-family:myFirstFont;
}
</style>
```

# CSS3 2D 转换

## scale() 方法

```css
-ms-transform:scale(2,3); /* IE 9 */
-webkit-transform: scale(2,3); /* Safari */
transform: scale(2,3); /* 标准语法 */
```

scale（2,3）转变宽度为原来的大小的2倍，和其原始大小3倍的高度。

# CSS3 3D 转换

```css
div
{
    transform: rotateX(120deg);
    -webkit-transform: rotateX(120deg); /* Safari 与 Chrome */
}
```

# CSS3 过渡

```css
div
{
    transition: width 2s, height 2s, transform 2s;
    -webkit-transition: width 2s, height 2s, -webkit-transform 2s;
}
```

# CSS3 动画

## CSS3 @keyframes 规则

要创建 CSS3 动画，你需要了解 @keyframes 规则。

@keyframes 规则是创建动画。

@keyframes 规则内指定一个 CSS 样式和动画将逐步从目前的样式更改为新的样式。

```css
@keyframes myfirst
{
    from {background: red;}
    to {background: yellow;}
}
 
@-webkit-keyframes myfirst /* Safari 与 Chrome */
{
    from {background: red;}
    to {background: yellow;}
}
```

## CSS3 动画

当在 **@keyframes** 创建动画，把它绑定到一个选择器，否则动画不会有任何效果。

指定至少这两个CSS3的动画属性绑定向一个选择器：

- 规定动画的名称
- 规定动画的时长

```css
div
{
    animation: myfirst 5s;
    -webkit-animation: myfirst 5s; /* Safari 与 Chrome */
}
```

# CSS3 多列

## CSS3 创建多列

`column-count` 属性指定了需要分割的列数。

```css
div {
    -webkit-column-count: 3; /* Chrome, Safari, Opera */
    -moz-column-count: 3; /* Firefox */
    column-count: 3;
}
```

## CSS3 多列中列与列间的间隙

`column-gap` 属性指定了列与列间的间隙。

```css
div {
    -webkit-column-gap: 40px; /* Chrome, Safari, Opera */
    -moz-column-gap: 40px; /* Firefox */
    column-gap: 40px;
}
```

## 指定元素跨越多少列

```css
h2 {
    -webkit-column-span: all; /* Chrome, Safari, Opera */
    column-span: all;
}
```

# CSS3 用户界面

## CSS3 调整尺寸(Resizing)

CSS3中，resize属性指定一个元素是否应该由用户去调整大小。

```css
div
{
    resize:both;
    overflow:auto;
}
```

# CSS 图片

## 图片滤镜

CSS `filter` 属性用为元素添加可视效果 (例如：模糊与饱和度) 。

```css
img {
    -webkit-filter: grayscale(100%); /* Chrome, Safari, Opera */
    filter: grayscale(100%);
}
```

# CSS 按钮

## 禁用按钮

```css
.disabled {
    opacity: 0.6;
    cursor: not-allowed;
}
```

# CSS3 框大小

## 使用 CSS3 box-sizing 属性

CSS3 `box-sizing` 属性在一个元素的 width 和 height 中包含 padding(内边距) 和 border(边框)。

如果在元素上设置了 `box-sizing: border-box;` 则 padding(内边距) 和 border(边框) 也包含在 width 和 height 中

# CSS3 弹性盒子(Flex Box)

弹性盒子由弹性容器(Flex container)和弹性子元素(Flex item)组成。

弹性容器通过设置 display 属性的值为 flex 或 inline-flex将其定义为弹性容器。

弹性容器内包含了一个或多个弹性子元素。

## flex-direction

`flex-direction` 属性指定了弹性子元素在父容器中的位置。

### 语法

```css
flex-direction: row | row-reverse | column | column-reverse
```

## justify-content 属性

内容对齐（justify-content）属性应用在弹性容器上，把弹性项沿着弹性容器的主轴线（main axis）对齐。

justify-content 语法如下：

```css
justify-content: flex-start | flex-end | center | space-between | space-around
```

![img](https://www.runoob.com/wp-content/uploads/2016/04/2259AD60-BD56-4865-8E35-472CEABF88B2.jpg)

## align-items 属性

`align-items` 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式。

```css
align-items: flex-start | flex-end | center | baseline | stretch
```

## 弹性子元素属性

### 排序

`order` 属性设置弹性容器内弹性子元素的属性:

```css
.flex-item {
    background-color: cornflowerblue;
    width: 100px;
    height: 100px;
    margin: 10px;
}
 
.first {
    -webkit-order: -1;
    order: -1;
}
```

# CSS3 多媒体查询

## CSS3 多媒体类型

|   值   |               描述               |
| :----: | :------------------------------: |
|  all   |      用于所有多媒体类型设备      |
| print  |            用于打印机            |
| screen | 用于电脑屏幕，平板，智能手机等。 |
| speech |          用于屏幕阅读器          |

## 520 到 699px 宽度 - 添加邮箱图标

```css
@media screen and (max-width: 699px) and (min-width: 520px) {
    ul li a {
        padding-left: 30px;
        background: url(email-icon.png) left center no-repeat;
    }
}
```

