# JavaScript Array 对象

对象包括属性和方法。

## 数组属性

| 属性                                                         | 描述                             |
| :----------------------------------------------------------- | :------------------------------- |
| [constructor](https://www.runoob.com/jsref/jsref-constructor-array.html) | 返回创建数组对象的原型函数。     |
| [length](https://www.runoob.com/jsref/jsref-length-array.html) | 设置或返回数组元素的个数。       |
| [prototype](https://www.runoob.com/jsref/jsref-prototype-array.html) | 允许你向数组对象添加属性或方法。 |

```js
一个新的数组的方法，将数组值转为大写：
Array.prototype.myUcase=function()
{
    for (i=0;i<this.length;i++)
    {
        this[i]=this[i].toUpperCase();
    }
}

创建一个数组，然后调用 myUcase 方法：
var fruits=["Banana","Orange","Apple","Mango"];
fruits.myUcase();

fruits 数组现在的值为：
BANANA,ORANGE,APPLE,MANGO
```

prototype 属性使您有能力向对象添加属性和方法。

当构建一个属性，所有的数组将被设置属性，它是默认值。

在构建一个方法时，所有的数组都可以使用该方法。

# Window 对象

## Window 对象

Window 对象表示浏览器中打开的窗口。

如果文档包含框架（<frame> 或 <iframe> 标签），浏览器会为 HTML 文档创建一个 window 对象，并为每个框架创建一个额外的 window 对象。

# HTML DOM Document 对象

## HTML DOM 节点

在 HTML DOM (Document Object Model) 中 , 每一个元素都是 **节点**:

- 文档是一个文档节点。
- 所有的HTML元素都是元素节点。
- 所有 HTML 属性都是属性节点。
- 文本插入到 HTML 元素是文本节点。are text nodes。
- 注释是注释节点。

# HTML DOM 事件

## HTML DOM 事件

HTML DOM 事件允许Javascript在HTML文档元素中注册不同事件处理程序。

事件通常与函数结合使用，函数不会在事件发生前被执行！ (如用户点击按钮)。

## 鼠标事件

| 属性                                                         | 描述                                   | DOM  |
| :----------------------------------------------------------- | :------------------------------------- | :--- |
| [onclick](https://www.runoob.com/jsref/event-onclick.html)   | 当用户点击某个对象时调用的事件句柄。   | 2    |
| [oncontextmenu](https://www.runoob.com/jsref/event-oncontextmenu.html) | 在用户点击鼠标右键打开上下文菜单时触发 |      |
| [ondblclick](https://www.runoob.com/jsref/event-ondblclick.html) | 当用户双击某个对象时调用的事件句柄。   | 2    |
| [onmousedown](https://www.runoob.com/jsref/event-onmousedown.html) | 鼠标按钮被按下。                       | 2    |
| [onmouseenter](https://www.runoob.com/jsref/event-onmouseenter.html) | 当鼠标指针移动到元素上时触发。         | 2    |
| [onmouseleave](https://www.runoob.com/jsref/event-onmouseleave.html) | 当鼠标指针移出元素时触发               | 2    |
| [onmousemove](https://www.runoob.com/jsref/event-onmousemove.html) | 鼠标被移动。                           | 2    |
| [onmouseover](https://www.runoob.com/jsref/event-onmouseover.html) | 鼠标移到某元素之上。                   | 2    |
| [onmouseout](https://www.runoob.com/jsref/event-onmouseout.html) | 鼠标从某元素移开。                     | 2    |
| [onmouseup](https://www.runoob.com/jsref/event-onmouseup.html) | 鼠标按键被松开。                       | 2    |

# DOM HTMLCollection

HTMLCollection 是 HTML 元素的集合。

HTMLCollection 对象类似一个包含 HTML 元素的数组列表。

[getElementsByTagName()](https://www.runoob.com/jsref/met-element-getelementsbytagname.html) 方法返回的就是一个 HTMLCollection 对象。