## 外部脚本

外部脚本很实用，如果相同的脚本被用于许多不同的网页。

JavaScript 文件的文件扩展名是 *.js*。

如需使用外部脚本，请在 <script> 标签的 src (source) 属性中设置脚本的名称：

```html
<script src="myScript.js"></script>
```

## 外部 JavaScript 的优势

在外部文件中放置脚本有如下优势：

- 分离了 HTML 和代码
- 使 HTML 和 JavaScript 更易于阅读和维护
- 已缓存的 JavaScript 文件可加速页面加载

如需向一张页面添加多个脚本文件 - 请使用多个 script 标签：

```html
<script src="myScript1.js"></script>
<script src="myScript2.js"></script>
```

## 使用 document.write()

**注意：**在 HTML 文档完全加载后使用 **document.write()** 将*删除所有已有的 HTML* ：

```html
<!DOCTYPE html>
<html>
<body>

<h1>我的第一张网页</h1>

<p>我的第一个段落</p>

<button onclick="document.write(5 + 6)">试一试</button>

</body>
</html>
```

**提示：****document.write()** 方法仅用于测试。

## 分号 ;

分号分隔 JavaScript 语句。

请在每条可执行的语句之后添加分号：

```js
a = 5;
b = 6;
c = a + b;
```

如果有分号分隔，允许在同一行写多条语句：

```js
a = 5; b = 6; c = a + b;
```

您可能在网上看到不带分号的例子。

**提示：**以分号结束语句不是必需的，但我们仍然强烈建议您这么做。

## JavaScript 行长度和折行

为了达到最佳的可读性，程序员们常常喜欢把代码行控制在 80 个字符以内。

如果 JavaScript 语句太长，对其进行折行的最佳位置是某个运算符：

```js
document.getElementById("demo").innerHTML =
 "Hello Kitty.";
```

## JavaScript 关键词

| 关键词        | 描述                                              |
| :------------ | :------------------------------------------------ |
| break         | 终止 switch 或循环。                              |
| continue      | 跳出循环并在顶端开始。                            |
| debugger      | 停止执行 JavaScript，并调用调试函数（如果可用）。 |
| do ... while  | 执行语句块，并在条件为真时重复代码块。            |
| for           | 标记需被执行的语句块，只要条件为真。              |
| function      | 声明函数。                                        |
| if ... else   | 标记需被执行的语句块，根据某个条件。              |
| return        | 退出函数。                                        |
| switch        | 标记需被执行的语句块，根据不同的情况。            |
| try ... catch | 对语句块实现错误处理。                            |
| var           | 声明变量。                                        |

## JavaScript 标识符

标识符是名称。

在 JavaScript 中，标识符用于命名变量（以及关键词、函数和标签）。

在大多数编程语言中，合法名称的规则大多相同。

在 JavaScript 中，首字符必须是字母、下划线（-）或美元符号（$）。

连串的字符可以是字母、数字、下划线或美元符号。

**提示：**数值不可以作为首字符。这样，JavaScript 就能轻松区分标识符和数值。

## JavaScript 与驼峰式大小写

JavaScript 程序员倾向于使用以小写字母开头的驼峰大小写：

```js
firstName, lastName, masterCard, interCity
```

## 一条语句，多个变量

您可以在一条语句中声明许多变量。

以 var 作为语句的开头，并以*逗号*分隔变量：

```js
var person = "Bill Gates", carName = "porsche", price = 15000;
```

声明可横跨多行：

```js
var person = "Bill Gates",
carName = "porsche",
price = 15000;
```

## JavaScript 字符串运算符

\+ 运算符也可用于对字符串进行相加（concatenate，级联）。

**提示：**在用于字符串时，**+** 运算符被称为级联运算符。

## 幂

x ** y 产生的结果与 Math.pow(x,y) 相同:

## JavaScript 数值

JavaScript 只有一种数值类型。

超大或超小的数值可以用科学计数法来写：

```js
var y = 123e5;      // 12300000
var z = 123e-5;     // 0.00123
```

## Undefined

在 JavaScript 中，没有值的变量，其值是 undefined。typeof 也返回 undefined。

任何变量均可通过设置值为 undefined 进行清空。其类型也将是 undefined。

## 复杂数据

```js
typeof {name:'Bill', age:62} // 返回 "object"
typeof [1,2,3,4]             // 返回 "object" (并非 "array"，参见下面的注释)
typeof null                  // 返回 "object"
typeof function myFunc(){}   // 返回 "function"
```

## 局部变量

在 JavaScript 函数中声明的变量，会成为函数的*局部变量*。

局部变量只能在函数内访问。

## 对象方法

对象也可以有*方法*。

方法是在对象上执行的*动作*。

方法以*函数定义*被存储在属性中。

方法是作为属性来存储的函数。

```js
var person = {
  firstName: "Bill",
  lastName : "Gates",
  id       : 678,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

## 访问对象属性

您能够以两种方式访问属性：

```js
objectName.propertyName
或者
objectName["propertyName"]
```

## 字符串可以是对象

```js
var x = new String("Bill");             
var y = new String("Bill");

// (x === y) 为 false，因为 x 和 y 是不同的对象
```

## String.trim()

trim() 方法删除字符串两端的空白符：

```js
var str = "       Hello World!        ";
alert(str.trim());
```

## 把字符串转换为数组

可以通过 split() 将字符串转换为数组：

```js
let str = 'abcd';
li = str.split('');
console.log(li);

[ 'a', 'b', 'c', 'd' ]
```

## NaN - 非数值

```js
typeof NaN;             // 返回 "number"
```

## 位移元素

位移与弹出等同，但处理首个元素而不是最后一个。

shift() 方法会删除首个数组元素，并把所有其他元素“位移”到更低的索引。

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();            // 从 fruits 删除第一个元素 "Banana"
```

## 回调函数

回调函数即函数作为参数



空指针对象null