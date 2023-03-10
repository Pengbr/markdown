# JavaScript 教程

# JavaScript 用法

HTML 中的脚本必须位于 <script> 与 </script> 标签之间。脚本可被放置在 HTML 页面的 <body> 和 <head> 部分中。

## 外部的 JavaScript

可以把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码。外部 JavaScript 文件的文件扩展名是 .js。如需使用外部文件，请在 <script> 标签的 "src" 属性中设置该 .js 文件

# Chrome 浏览器中执行 JavaScript

使用开发者工具

# JavaScript 输出

JavaScript 可以通过不同的方式来输出数据：

- 使用 **window.alert()** 弹出警告框。
- 使用 **document.write()** 方法将内容写到 HTML 文档中。
- 使用 **innerHTML** 写入到 HTML 元素。
- 使用 **console.log()** 写入到浏览器的控制台。

程序中调试是测试，查找及减少bug(错误)的过程。

# JavaScript 语法

## JavaScript 字面量

在编程语言中，一般固定值称为字面量，如 3.14。**数字（Number）字面量** 可以是整数或者是小数，或者是科学计数(e)。

## JavaScript 变量

在编程语言中，变量用于存储数据值。JavaScript 使用关键字 **var** 来定义变量， 使用等号来为变量赋值：

```js
var x, length

x = 5

length = 6
```

# JavaScript 语句

## 分号 ;

分号用于分隔 JavaScript 语句。通常我们在每条可执行的语句结尾添加分号。使用分号的另一用处是在一行中编写多条语句。

```javascript
a = 5; b = 6; c = a + b;
```

## 对代码行进行折行

```js
document.write("你好 \
世界!");
```

# JavaScript 数据类型

## JavaScript 拥有动态类型

JavaScript 拥有动态类型。这意味着相同的变量可用作不同的类型：

```js
var x;               // x 为 undefined
var x = 5;           // 现在 x 为数字
var x = "John";      // 现在 x 为字符串
```

JavaScript 变量均为对象。当您声明一个变量时，就创建了一个新的对象。

# JavaScript 对象

JavaScript 对象是拥有属性和方法的数据。

![image-20210314113618478](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210314113618478.png)

![image-20210401093209752](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210401093209752.png)

# JavaScript 作用域

局部变量在函数开始执行时创建，函数执行完后局部变量会自动销毁。

如果变量在函数内没有声明（没有使用 var 关键字），该变量为全局变量。

以下实例中 carName 在函数内，但是为全局变量。

```js
// 此处可调用 carName 变量
 
function myFunction() {
    carName = "Volvo";
    // 此处可调用 carName 变量
}
```

# JavaScript 函数

同python基本一致

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>测试实例</title>
<script>
function myFunction()
{
    alert("Hello World!");
}
</script>
</head>
 
<body>
<button onclick="myFunction()">点我</button>
</body>
</html>
```

```html
<p>点击这个按钮，来调用带参数的函数。</p>
<button onclick="myFunction('Harry Potter','Wizard')">点击这里</button>
<script>
function myFunction(name,job){
    alert("Welcome " + name + ", the " + job);
}
</script>
```

# JavaScript 事件

HTML 事件是发生在 HTML 元素上的事情。

当在 HTML 页面中使用 JavaScript 时， JavaScript 可以触发这些事件。

```html
<button onclick="getElementById('demo').innerHTML=Date()">现在的时间是?</button>
```

以上实例中，JavaScript 代码将修改 id="demo" 元素的内容。

在下一个实例中，代码将修改自身元素的内容 (使用 **this**.innerHTML):

```html
<button onclick="this.innerHTML=Date()">现在的时间是?</button>
```

# JavaScript 字符串

## 字符串长度

```js
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;
```

# JavaScript 运算符

## 对字符串和数字进行加法运算

两个数字相加，返回数字相加的和，如果数字与字符串相加，返回字符串，如下实例：

```js
x=5+5;
y="5"+5;
z="Hello"+5;

x,y, 和 z 输出结果为:
10
55
Hello5
```

**规则:**如果把数字与字符串相加，结果将成为字符串！

# JavaScript 比较 和 逻辑运算符

## 条件运算符(类似三元运算符)

### 实例

如果变量 age 中的值小于 18，则向变量 voteable 赋值 "年龄太小"，否则赋值 "年龄已达到"。

```js
voteable=(age<18)?"年龄太小":"年龄已达到";
```

# JavaScript switch 语句

```js
// 注意switch后的数据类型要与case后的数据类型一致
var d=new Date().getDay();
switch (d)
{
    case 6:x="今天是星期六";
    break;
    case 0:x="今天是星期日";
    break;
    default:
    x="期待周末";
}
document.getElementById("demo").innerHTML=x;
```

# JavaScript for 循环

## For/In 循环

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
	
<p>点击下面的按钮，循环遍历对象 "person" 的属性。</p>
<button onclick="myFunction()">点击这里</button>
<p id="demo"></p>
<script>
function myFunction(){
	var x;
	var txt="";
	var person={fname:"Bill",lname:"Gates",age:56}; 
	for (x in person){
		txt=txt + person[x];
	}
	document.getElementById("demo").innerHTML=txt;
}
</script>
	
</body>
</html>
```

# JavaScript while 循环

## do/while 循环

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>点击下面的按钮，只要 i 小于 5 就一直循环代码块。</p>
<button onclick="myFunction()">点击这里</button>
<p id="demo"></p>
<script>
function myFunction(){
	var x="",i=0;
	do{
		x=x + "该数字为 " + i + "<br>";
	    i++;
	}
	while (i<5)  
	document.getElementById("demo").innerHTML=x;
}
</script>

</body>
</html>
```

# JavaScript break 和 continue 语句

## JavaScript 标签

如需标记 JavaScript 语句，请在语句之前加上冒号：

label: statements

break 和 continue 语句仅仅是能够跳出代码块的语句。

语法:

break labelname;   continue labelname;

```js
cars=["BMW","Volvo","Saab","Ford"];
list: 
{
    document.write(cars[0] + "<br>"); 
    document.write(cars[1] + "<br>"); 
    document.write(cars[2] + "<br>"); 
    break list;
    document.write(cars[3] + "<br>"); 
    document.write(cars[4] + "<br>"); 
    document.write(cars[5] + "<br>"); 
}
```

# JavaScript typeof, null, 和 undefined

## typeof 操作符

你可以使用 typeof 操作符来检测变量的数据类型。

```js
typeof "John"                // 返回 string
typeof 3.14                  // 返回 number
typeof false                 // 返回 boolean
typeof [1,2,3,4]             // 返回 object
typeof {name:'John', age:34} // 返回 object
// 在js中除了基本数据类型外，一切皆对象
```

## undefined 和 null 的区别

```js
typeof undefined             // undefined
typeof null                  // object
null === undefined           // false
null == undefined            // true
```

# JavaScript 类型转换

## 一元运算符 +

**Operator +** 可用于将变量转换为数字：

```js
var y = "5";      // y 是一个字符串
var x = + y;      // x 是一个数字
```

# JavaScript 正则表达式

正则表达式（英语：Regular Expression，在代码中常简写为regex、regexp或RE）使用单个字符串来描述、匹配一系列符合某个句法规则的字符串搜索模式。

搜索模式可用于文本搜索和文本替换。

## 什么是正则表达式？

正则表达式是由一个字符序列形成的搜索模式。

当你在文本中搜索数据时，你可以用搜索模式来描述你要查询的内容。

正则表达式可以是一个简单的字符，或一个更复杂的模式。

正则表达式可用于所有文本搜索和文本替换的操作。

## 语法

```js
/正则表达式主体/修饰符(可选)
```

```js
// 正则表达式用于定义一些字符串的规则，计算机根据正则表达式来检查一个字符串是否符合规则，将字符串中符合规则的提取出来
// 创建正则表达式的对象，需要两个参数，正则表达式、匹配模式   regular expression
// 匹配模式可选值：i(ignore) 忽略大小写  g(global) 全局匹配模式
var reg =new RegExp('abC','i');
console.log(reg);

var result=reg.test('Abc'); // 检查字符串是否符合正则表达式规则
console.log(result);

// 使用字面量来创建正则表达式  语法：var 变量=/正则表达式/匹配模式
var reg=/a/i;
console.log(reg.test('abc'));

reg=/a|b|c/; // a或b或c |或的意思
console.log(reg.test('a'));

reg=/[a-z]/i; // []里的内容也是或的关系
console.log(reg.test('G'));

reg=/a[bde]c/; 
console.log(reg.test('aec'));

reg=/[^ab]/; // [^] 除了
console.log(reg.test('c'));

reg=/[0-9]/;
console.log(reg.test('123'));

// 量词，通过设置量词可以设置一个内容出现的次数
// ab为一组，出现一到三次
reg=/(ab){1,3}/;
console.log(reg.test('abab'));

// +表示至少一个，*表示零个或多个，？表示零个或一个
reg=/ab+c/;
console.log(reg.test('abbc'));

reg=/^a|c$/; // ^表示开头,$表示结尾
console.log(reg.test('abvc'));

reg=/^1[3-9][0-9]{9}$/;
console.log(reg.test('15810255877'));

reg=/\./; // .表示任意字符,要表示单纯的点需要转义
console.log(reg.test('abc.'));

// \w  \s  \d  \b 等等
reg=/\w/; // \w表示任意字母数字下划线，\W与\w正好相反
console.log(reg.test('abc'));
// \d 表示任意数字，\s 表示空格, \b 表示单词边界
reg=/\bchild\b/;
console.log(reg.test('children'));

reg=/\w+@[A-z0-9]+\.[A-z]{2,5}/;
console.log(reg.test('1303089388@qq.com'));
```

# JavaScript 声明提升

JavaScript 中，函数及变量的声明都将被提升到函数的最顶部。

JavaScript 中，变量可以在使用后声明，也就是变量可以先使用再声明。

## JavaScript 初始化不会提升

JavaScript 只有声明的变量会提升，初始化的不会。

# JavaScript 严格模式(use strict)

JavaScript 严格模式（strict mode）即在严格的条件下运行。

## 使用 "use strict" 指令

"use strict" 指令在 JavaScript 1.8.5 (ECMAScript5) 中新增。

它不是一条语句，但是是一个字面量表达式，在 JavaScript 旧版本中会被忽略。

"use strict" 的目的是指定代码在严格条件下执行。

严格模式下你不能使用未声明的变量。

```js
"use strict";
myFunction();

function myFunction() {
    y = 3.14;   // 报错 (y 未定义)
}
```

# JavaScript 使用误区

## JavaScript 字符串分行

字符串断行需要使用反斜杠(\)，如下所示:                   ***同python***

```js
var x = "Hello \
World!";
```

## 程序块作用域

在每个代码块中 JavaScript 不会创建一个新的作用域，一般各个代码块的作用域都是全局的。

以下代码的的变量 i 返回 10，而不是 undefined：

```js
for (var i = 0; i < 10; i++) {
    // some code
}
return i;
```

# JavaScript this 关键字

面向对象语言中 this 表示当前对象的一个引用。

但在 JavaScript 中 this 不是固定不变的，它会随着执行环境的改变而改变。

- 在方法中，this 表示该方法所属的对象。
- 如果单独使用，this 表示全局对象。
- 在函数中，this 表示全局对象。
- 在函数中，在严格模式下，this 是未定义的(undefined)。
- 在事件中，this 表示接收事件的元素。
- 类似 call() 和 apply() 方法可以将 this 引用到任何对象。

## 事件中的 this

在 HTML 事件句柄中，this 指向了接收事件的 HTML 元素：

```html
<button onclick="this.style.display='none'">
点我后我就消失了
</button>
```

## 显式函数绑定

在 JavaScript 中函数也是对象，对象则有方法，apply 和 call 就是函数对象的方法。这两个方法异常强大，他们允许切换函数执行的上下文环境（context），即 this 绑定的对象。

在下面实例中，当我们使用 person2 作为参数来调用 person1.fullName 方法时, **this** 将指向 person2, 即便它是 person1 的方法：

```js
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
person1.fullName.call(person2);  // 返回 "John Doe"
```

事件对象event可以默认申明

event.offsetX 原点为事件元素左上角    event.clientX 原点为窗口左上角   event.pageX  原点为页面左上角

return false取消默认行为

事件委托：将多个子元素的事件监听委托给父辈元素处理

xml用来存储和传输数据，类似json,目前已被json取代

通过ajax请求从前台拿到后端的数据

# ES6

对象解构可以取别名

```javascript
let obj = {
    name:'br',
    age:22
}
let {name:MyName} = obj
console.log(MyName)
```

数组的解构

```javascript
let arr1 = [10,20,30]
let [a,b,c] = arr1
console.log(a,b,c)
```

函数参数的解构

```javascript
function func({name,age}){
    console.log(name,age)
}

func(obj)
```

合并其它对象

```javascript
let newObj = Object.assign({},obj1,obj2)
console.log(newObj)
```

箭头函数没有自己的作用域，作用域和外层相同

```javascript
function People(name,age){
    this.name = name
    this.age = age
    this.say = function(){
        let _this = this
        setTimeout(
            // function有自己的作用域
            function(){
            console.log(_this.name)
        },1000)
    }
}

class People{
   construtor(name,age){
        this.name=name
        this.age=age
    }
   say(){
       setTimeout(()=>{
           console.log(this.name)
       },1000)
   }
}
```

export default一个文件只能有一个

# 字符串常见方法

split方法：split 方法:将一个字符串分割为子字符串,然后将结果作为字符串数组返回。



数组解构与对象解构

es6中注意区分export与export default

1、export default 向外暴露的成员，可以使用任意变量来接收

2、在一个模块中，export default 只允许向外暴露一次

3、在一个模块中，可以同时使用export default 和export 向外暴露成员

4、使用export向外暴露的成员，只能使用{  }的形式来接收，这种形式，叫做【按需导出】

5、export可以向外暴露多个成员，同时，如果某些成员，在import导入时，不需要，可以不在{ }中定义

6、使用export导出的成员，必须严格按照导出时候的名称，来使用{ }按需接收

7、使用export导出的成员，如果想换个变量名称接收，可以使用as来起别名
