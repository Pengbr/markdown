# HTML 教程- (HTML5 标准)

**注意：***对于中文网页需要使用* **<meta charset="utf-8">** *声明编码，否则会出现乱码。有些浏览器(如 360 浏览器)会设置 GBK 为默认编码，则你需要设置为* **<meta charset="gbk">。**

# HTML 简介

HTML 不是一种编程语言，而是一种**标记**语言

<b></b>  b标签加粗

# HTML 元素

HTML 标签对大小写不敏感：<P> 等同于 <p>。许多网站都使用大写的 HTML 标签。

# HTML 属性

属性一般描述于**开始标签**

双引号是最常用的，不过使用单引号也没有问题。

**提示:** 在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：name='John "ShotGun" Nelson'

# HTML 标题

<hr> 标签在 HTML 页面中创建水平线。

###### 标题大小与字体大小的关系

1到6号标题与1到6号字体逆序对应，比如1号字体对应6号标题，2号字体对应5号标题。

```html
<h1>这是1号标题</h1>
<font size="6" color="red">这是6号字体文本</font>
```

# HTML 段落

**注意：**浏览器会自动地在段落的前后添加空行。（</p> 是块级元素）

当显示页面时，浏览器会移除源代码中多余的空格和空行。所有连续的空格或空行都会被算作一个空格。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为一个空格。

# HTML 文本格式化

HTML 使用标签 <b>("bold") 与 <i>("italic") 对输出的文本进行格式, 如：**粗体** or *斜体*

<small> 定义小字号    <sub>定义下标字   <sup>定义上标字  <ins>定义插入字  <del>定义删除字

<code>定义计算机代码  <kbd>定义键盘码  <samp>定义计算机代码样本  <var>定义变量  

<pre>定义预定义格式文本   <abbr>定义缩写   <address>定义地址   <bdo>定义文字方向

<q>定义短的引用   <cite>定义引用、引证   <dfn>定义一个定义项目

# HTML 链接

超链接可以是一个字，一个词，或者一组词，也可以是一幅图像，您可以点击这些内容来跳转到新的文档或者当前文档中的某个部分。当您把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手。

如果你将 target 属性设置为 "_blank", 链接将在新窗口打开。

# HTML <head>

[ - 定义了所有链接的URL](https://www.runoob.com/try/try.php?filename=tryhtml_base)
使用 <base> 定义页面中所有链接默认的链接目标地址。

```html
<head>
<base href="http://www.runoob.com/images/" target="_blank">
</head>
```

# HTML 样式- CSS

CSS 可以通过以下方式添加到HTML中:

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 <head> 区域使用**<style>** **元素** 来包含CSS
- 外部引用 - 使用外部 CSS **文件**

# HTML 图像

### HTML 图像- 图像标签（ <img>）和源属性（Src）

**定义图像的语法是：**

<img src="url" alt="some_text">

### HTML 图像- Alt属性

alt 属性用来为图像定义一串预备的可替换的文本。替换文本属性的值是用户定义的。

<img src="boat.gif" alt="Big Boat">

在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。此时，浏览器将显示这个替代性的文本而不是图像。为页面上的图像都加上替换文本属性是个好习惯，这样有助于更好的显示信息，并且对于那些使用纯文本浏览器的人来说是非常有用的。

# HTML 表格

表格由 <table> 标签来定义。每个表格均有若干行（由 <tr> 标签定义），每行被分割为若干单元格（由 <td> 标签定义）。字母 td 指表格数据（table data），即数据单元格的内容。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

表格的表头使用 <th> 标签进行定义。大多数浏览器会把表头显示为粗体居中的文本

![image-20210130193735880](C:\Users\HP1\AppData\Roaming\Typora\typora-user-images\image-20210130193735880.png)

# HTML 列表

HTML 支持有序、无序和定义列表:

![image-20210131190742663](C:\Users\HP1\AppData\Roaming\Typora\typora-user-images\image-20210131190742663.png)

# HTML <div> 和<span>

大多数 HTML 元素被定义为**块级元素**或**内联元素**。块级元素在浏览器显示时，通常会以新行来开始（和结束）。实例: <h1>, <p>, <ul>, <table>内联元素在显示时通常不会以新行开始。实例: <b>, <td>, <a>, <img>

# HTML 表单和输入

表单是一个包含表单元素的区域。

表单元素是允许用户在表单中输入内容,比如：文本域(textarea)、下拉列表、单选框(radio-buttons)、复选框(checkboxes)等等。

表单使用表单标签 <form> 来设置:

<form>
.
*input 元素*
.
</form>
# HTML 框架

通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。网页里面嵌套网页。

**iframe语法:**

<iframe src="URL"></iframe>

该URL指向不同的网页。

# HTML 颜色

HTML 颜色由红色、绿色、蓝色混合而成。

HTML 颜色由一个十六进制符号来定义，这个符号由红色、绿色和蓝色的值组成（RGB）。

每种颜色的最小值是0（十六进制：#00）。最大值是255（十六进制：#FF）。

# HTML 颜色名

# HTML 颜色值

十六进制值的写法为 # 号后跟三个或六个十六进制字符。

三位数表示法为：#RGB，转换为6位数表示为：#RRGGBB。

# HTML 脚本

JavaScript 使 HTML 页面具有更强的动态和交互性。

## HTML <script> 标签

<script> 标签用于定义客户端脚本，比如 JavaScript。

<script> 元素既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

## HTML<noscript> 标签

<noscript> 标签提供无法使用脚本时的替代内容，比方在浏览器禁用脚本时，或浏览器不支持客户端脚本时。

<noscript>元素可包含普通 HTML 页面的 body 元素中能够找到的所有元素。

# HTML 字符实体

格式：&实体名；

# HTML 统一资源定位器(Uniform Resource Locators)

**scheme`://`host.domain`:`port`/`path`/`filename**

- scheme - 定义因特网服务的类型。最常见的类型是 http
- host - 定义域主机（http 的默认主机是 www）
- domain - 定义因特网域名，比如 runoob.com
- :port - 定义主机上的端口号（http 的默认端口号是 80）
- path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。
- filename - 定义文档/资源的名称

# HTML 速查列表

canvas是H5新标签