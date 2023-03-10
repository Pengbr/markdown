python

在终端调用命令：将可执行程序的路径添加到环境变量即可

ctrl+/ 进入源代码模式

```python
print('hello world')
```

```javascript
document.write('hello world')
```

**markdown中使用标识符$$即可表示引入latex语法**
$$
f(x;\mu,\sigma^2)=\frac{1}{sigma\sqrt{2\pi}}e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}\tag{1}
$$



not()逻辑取反

# Python 3 教程

# Python3 基础语法

## python保留字

保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：

```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠(\)来实现多行语句，例如：

```python
total = item_one + \
        item_two + \
        item_three
```

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠(\)，例如：

```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

## 同一行显示多条语句

Python可以在同一行中使用多条语句，语句之间使用分号(;)分割，以下是一个简单的实例：

```python
#!/usr/bin/python3
 
import sys; x = 'runoob'; sys.stdout.write(x + '\n')
```

# Python3 基本数据类型、运算符

Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。

注意区分可变数据类型和不可变数据类型

海象运算符：=

逻辑运算符的优先级是not>and>or

# Python3 字符串

| \a   | 响铃                                                         | `>>> print("\a")`执行后电脑有响声。                          |
| ---- | :----------------------------------------------------------- | ------------------------------------------------------------ |
| \r   | 回车，将 **\r** 后面的内容移到字符串开头，并逐一替换开头部分的字符，直至将 **\r** 后面的内容完全替换完成。 | `>>> print("Hello\rWorld!") World! >>> print('google runoob taobao\r123456') 123456 runoob taobao` |

## Python字符串格式化

```python
#!/usr/bin/python3
 
print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
```

| 符  号 |                 描述                 |
| :----: | :----------------------------------: |
|   %c   |        格式化字符及其ASCII码         |
|   %s   |             格式化字符串             |
|   %d   |              格式化整数              |
|   %u   |           格式化无符号整型           |
|   %o   |         格式化无符号八进制数         |
|   %x   |        格式化无符号十六进制数        |
|   %X   |    格式化无符号十六进制数（大写）    |
|   %f   | 格式化浮点数字，可指定小数点后的精度 |
|   %e   |       用科学计数法格式化浮点数       |
|   %E   |  作用同%e，用科学计数法格式化浮点数  |
|   %g   |             %f和%e的简写             |
|   %G   |           %f 和 %E 的简写            |
|   %p   |     用十六进制数格式化变量的地址     |

# Python3 列表

## 嵌套列表

使用嵌套列表即在列表里创建其它列表，例如：

```python
>>>a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```

# Python3 函数

加了星号 ***** 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。

```python
#!/usr/bin/python3
  
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )
```

```python
输出: 
70
(60, 50)
```

加了两个星号 ***\*** 的参数会以字典的形式导入。

```python
#!/usr/bin/python3
  
# 可写函数说明
def printinfo( arg1, **vardict ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vardict)
 
# 调用printinfo 函数
printinfo(1, a=2,b=3)
```

```python
输出: 
1
{'a': 2, 'b': 3}
```

## 匿名函数

```python
#!/usr/bin/python3
 
# 可写函数说明
sum = lambda arg1, arg2: arg1 + arg2
 
# 调用sum函数
print ("相加后的值为 : ", sum( 10, 20 ))
print ("相加后的值为 : ", sum( 20, 20 ))
```

# Python3 数据结构

## 遍历技巧

在字典中遍历时，关键字和对应的值可以使用 items() 方法同时解读出来：

```python
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

在序列中遍历时，索引位置和对应值可以使用 enumerate() 函数同时得到：

```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```

同时遍历两个或更多的序列，可以使用 zip() 组合：

```python
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```

# Python3 模块

## __name__属性

一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用__name__属性来使该程序块仅在该模块自身运行时执行。

```python
#!/usr/bin/python3
# Filename: using_name.py

if __name__ == '__main__':
   print('程序自身在运行')
else:
   print('我来自另一模块')
```

运行输出如下：

```python
$ python using_name.py
程序自身在运行

$ python
>>> import using_name
我来自另一模块
>>>
```

工程>包>模块>函数

# Python3 输入和输出

可选项 **:** 和格式标识符可以跟着字段名。 这就允许对值进行更好的格式化。 下面的例子将 Pi 保留到小数点后三位：

```python
>>> import math
>>> print('常量 PI 的值近似为 {0:.3f}。'.format(math.pi))
常量 PI 的值近似为 3.142。
```

# Python3 错误和异常

## 抛出异常

Python 使用 raise 语句抛出一个指定的异常。

```python
x = 10
if x > 5:
    raise Exception('x 不能大于 5。x 的值为: {}'.format(x))
```

# Python3 面向对象

类有一个名为 __init__() 的特殊方法（**构造方法**），该方法在类实例化时会自动调用，像下面这样：

```python
def __init__(self):
    self.data = []
```

类定义了 __init__() 方法，类的实例化操作会自动调用 __init__() 方法。如下实例化类 MyClass，对应的 __init__() 方法就会被调用:

```python
x = MyClass()
```

```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
 
 
s = student('ken',10,60,3)
s.speak()
```

```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
#另一个类，多重继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
 
#多重继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
```

# Python 交换变量

```python
# -*- coding: UTF-8 -*-
 
# Filename : test.py
# author by : www.runoob.com
 
# 用户输入
 
x = input('输入 x 值: ')
y = input('输入 y 值: ')
 
# 不使用临时变量
x,y = y,x
 
print('交换后 x 的值为: {}'.format(x))
print('交换后 y 的值为: {}'.format(y))
```

# Python3 迭代器与生成器

## 迭代器

for循环遍历的是可迭代对象

迭代器有两个基本的方法：**iter()** 和 **next()**。

字符串，列表或元组对象都可用于创建迭代器：

```python
>>> list=[1,2,3,4]
>>> it = iter(list)    # 创建迭代器对象
>>> print (next(it))   # 输出迭代器的下一个元素
1
>>> print (next(it))
2
>>>
```

迭代器对象可以使用常规for语句进行遍历：

```python
#!/usr/bin/python3
 
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it:
    print (x, end=" ")
```

### 创建一个迭代器

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

__iter__() 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 __next__() 方法并通过 StopIteration 异常标识迭代的完成。

__next__() 方法（Python 2 里是 next()）会返回下一个迭代器对象。

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    x = self.a
    self.a += 1
    return x
 
myclass = MyNumbers()
myiter = iter(myclass)
 
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
```

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x)
```

## 生成器

在 Python 中，使用了 yield 的函数被称为生成器（generator）。

跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。

调用一个生成器函数，返回的是一个迭代器对象。

# 正则表达式

```python
import re

x = 'hello\\nworld'
# print(x)
# 第一个参数就是正则匹配规则，第二个参数表示需要匹配的字符串
m = re.search(r'\\', x)
print(m)

# match从头开始匹配，search是在整个字符串里面查找
m1 = re.match(r'good', 'hello world good morning')
print(m1)
m2 = re.search(r'good', 'hello world good morning')
print(m2)

# finditer返回可迭代对象
m3 = re.finditer(r'x', 'kxlxjxnxgx')
print(m3)
for t in m3:
    print(t)

m4 = re.findall(r'x\d+', 'klx3nx4fx5vsxox')
print(m4)

m5 = re.fullmatch(r'hello world', 'hello world')
print(m5)
```

dir()方法可以查看对象可以调用的方法
