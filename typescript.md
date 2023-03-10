安装 typescript：

npm install -g typescript

安装完成后我们可以使用 **tsc** 命令来执行 TypeScript 的相关代码，以下是查看版本号：

```typescript
$ tsc -v
Version 3.2.2
```

通常我们使用 **.ts** 作为 TypeScript 代码文件的扩展名。然后执行以下命令将 TypeScript 转换为 JavaScript 代码：

```typescript
tsc app.ts
```

![img](https://www.runoob.com/wp-content/uploads/2019/01/typescript_compiler.png)

数组类型 声明变量为数组。什么类型的数组

```typescript
// 在元素类型后面加上[]
let arr: number[] = [1, 2];

// 或者使用数组泛型
let arr: Array<number> = [1, 2];
```

元组 元组类型用来表示已知元素数量和类型的数组，各元素的类型不必相同，对应位置的类型需要相同。

```typescript
let x: [string, number];
x = ['Runoob', 1];    // 运行正常
x = [1, 'Runoob'];    // 报错
console.log(x[0]);    // 输出 Runoob
```

枚举 枚举类型用于定义数值集合。

```typescript
enum Color {Red, Green, Blue};
let c: Color = Color.Blue;
console.log(c);    // 输出 2
```

 可以用 | 来支持多种类型，示例代码如下：

```typescript
let x: number | null | undefined;
x = 1; // 运行正确
x = undefined;    // 运行正确
x = null;    // 运行正确
```

for...of 语句创建一个循环来迭代可迭代的对象。在 ES6 中引入的 for...of 循环，以替代 for...in 和 forEach() ，并支持新的迭代协议。for...of 允许你遍历 Arrays（数组）, Strings（字符串）, Maps（映射）, Sets（集合）等可迭代的数据结构等。

## 函数重载

重载是方法名字相同，而参数不同，返回类型可以相同也可以不同。

每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。

## 多维数组

一个数组的元素可以是另外一个数组，这样就构成了多维数组（Multi-dimensional Array）。

最简单的多维数组是二维数组，定义方式如下：

```typescript
var arr_name:datatype[][]=[ [val1,val2,val3],[v1,v2,v3] ]
```

## TypeScript 元组

我们知道数组中元素的数据类型都一般是相同的（any[] 类型的数组可以不同），如果存储的元素数据类型不同，则需要使用元组。

元组中允许存储不同类型的元素，元组可以作为参数传递给函数。

对象数组：

```typescript
const student : { sid : number, sname : string}[] = [
    {sid : 10001, sname : "张三"},
    {sid : 10002, sname : "李四"},
];
```

这样写起来代码的重用效果略差，此时我们可以定义一个类型别名，定义别名的时候要以`type`关键字声明。我们修改一下之前的代码：

```typescript
type student = {
    sid : number,
    sname : string
};

const FirstClass : student[] = [
    {sid : 10001, sname : "张三"},
    {sid : 10002, sname : "李四"}
];
```

 super 关键字是对父类的直接引用，该关键字可以引用父类的属性和方法。

## 访问控制修饰符

TypeScript 中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。TypeScript 支持 3 种不同的访问权限。

- **public（默认）** : 公有，可以在任何地方被访问。
- **protected** : 受保护，可以被其自身以及其子类和父类访问。
- **private** : 私有，只能被其定义所在的类访问。

## TypeScript 命名空间

命名空间一个最明确的目的就是解决重名问题。

命名空间是私有的，外部想访问的话需要export对外暴露。

假设这样一种情况，当一个班上有两个名叫小明的学生时，为了明确区分它们，我们在使用名字之外，不得不使用一些额外的信息，比如他们的姓（王小明，李小明），或者他们父母的名字等等。

命名空间定义了标识符的可见范围，一个标识符可在多个名字空间中定义，它在不同名字空间中的含义是互不相干的。这样，在一个新的名字空间中可定义任何标识符，它们不会与任何已有的标识符发生冲突，因为已有的定义都处于其他名字空间中。

TypeScript 中命名空间使用 **namespace** 来定义，语法格式如下：

```typescript
namespace SomeNameSpaceName { 
   export interface ISomeInterfaceName {      }  
   export class SomeClassName {      }  
}
```

## 装饰器

装饰器就是一个**方法**，类似于python的装饰器。可以保证原始代码不变的情况下扩展新的功能。

## 其它

ts-node可以直接在node的环境中运行typescript，而不用编译成JavaScript

抽象类和抽象方法规定了一个标准，和接口有点类似

extends继承，implements实现

**泛型：可以支持不特定的数据类型，要求传入的参数和返回的参数一致。泛型默认用大写字母T。当不确认参数类型时可以使用泛型。泛型的类型参数在调用时才确定。**
