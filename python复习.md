![image-20210310191645524](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210310191645524.png)

python的for循环可以与else搭配使用，当for循环正常结束时，else也会执行，而当for循环未正常结束，例如使用break提前退出时，则不会执行。

区分标识符与关键字，程序语言对各种变量、方法、函数等命名时使用的字符序列称为标识符，凡是可以自己命名的就是标识符。

go中下划线_本身是一个特殊的标识符，称为空标识符。可以代表任何其他字符，但是它对应的值会被忽略（比如：忽略某个返回值）。所以仅能被占位符使用，不能作为标识符使用。

go语言中&取址运算符，*取值运算符。

在程序语言中，往往越精确优先级越高。

![image-20210313110907981](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210313110907981.png)

两台机器是否ping通,ping通的话可以远程连接。

**函数式编程：函数即变量**    函数test,调用函数test().

```python
*args将参数以元组的形式传递给变量args,**kwargs将参数以字典的形式传给变量kwargs
# 倒入的是math里面的方法，math模块并没有导入
# from math import *
_age单下划线开头的是保护变量，__age双下划线开头的是私有变量
```

```python
class Student:  # class Student(object):也可以
    __slots__ = ('name','age','height')  # 这个属性直接定义在类里，是一个元组，用来规定对象可以存在的属性

    def __init__(self, name, age, height):  # 在__init__方法里，以参数的形式定义属性
        # self.name是对象的属性，name是参数
        self.name = name
        self.age = age
        self.height = height

    def say_hello(self):
        print('大家好，我是', self.name)

    def run(self):
        print('正在跑步')

    def eat(self):
        print('正在吃东西')


# Student()会自动调用__init__方法
# 1、Student()首先会调用__new__方法,申请内存地址
# 2、Student()调用__init__方法,并让self指向申请好的内存空间
# 3、让s1也指向创建好的内存空间
s1 = Student('小明', 18, 1.75)
s1.say_hello()
s1.run()
s1.eat()
# 动态语言,动态属性
s1.name = 'br'
print(s1.name)

s2 = Student('小美', 17, 1.65)
s2.eat()
```

```python
# 魔术方法
# import time


class Person(object):
    # 在创建对象时，会自动调用这个方法
    def __init__(self, name, age):
        print('__init__被调用了')
        self.name = name
        self.age = age

    # 当对象被销毁时，会自动调用这个方法
    # 程序走完后会自动销毁
    def __del__(self):
        print('del被调用了')

    def __repr__(self):
        return 'hello'

    def __str__(self):
        return f'{self.name},{self.age}'

    def __call__(self, *args, **kwargs):
        print('__call__方法被调用了')
        print(f'args={args},kwargs={kwargs}')
        fn = kwargs['fn']
        return  fn(args[0], args[1])


p = Person('张三', 18)
# del p
# 当打印一个对象的时候会调用这个对象的__str__或者__repr__方法
print(p)
print(p.__repr__())  # 魔术方法也可以手动调用
# time.sleep(10)

# print(repr({'name': 'zhangsan'}))
result = p(1, 2, fn=lambda x, y: x + y)  # 对象名()，调用__call__方法
print(result)
```

```python
class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __eq__(self, other):
        print('__eq__方法被调用了,other=', other)
        if self.name == other.name and self.age == other.age:
            return True


p1 = Person('张三', 18)
p2 = Person('张三', 18)
# ==会调用__eq__方法,若果不重写默认比较的是内存地址
print(hex(id(p1)))
print(hex(id(p2)))
print(p1 == p2)  # 本质是p1.__eq__(p2)
```

```python
class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age

    # 给自己定义的类重写内置方法
    def __eq__(self, other):
        if self.name == other.name and self.age == other.age:
            return True
        return False

    def __ne__(self, other):
        return 'hello'

    def __gt__(self, other):
        return self.age > other.age

    def __add__(self, other):
        return self.age + other.age

    def __mul__(self, other):
        return self.name * other


p1 = Person('张三', 19)
p2 = Person('李四', 18)
# !=本质是调用__ne__方法，或者__eq__方法取反
print(p1 != p2)
# >调用的是__gt__方法,>=调用的是__ge__方法,<调用的是__lt__方法,<=调用的是__le__方法
# +调用的是__add__方法,-调用的是__sub__方法,*调用的是__mul__方法,/调用的是__truediv__方法
# 幂运算调用__pow__方法,求模运算调用__mod__方法
# str()将对象转换为字符串，会自动调用__str__方法
# 同样int()会调用__int__方法，float()会调用__float__方法
print(p1 > p2)
print(p1 + p2)
print(p1 * 3)
```

```python
import datetime


class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age
        # 私有属性
        self.__money = 1000

    # def test(self):
    #     self.__money += 10

    def get_money(self):
        print(f'{datetime.datetime.now()}查询了余额')
        return self.__money

    def set_money(self, money):
        print('修改余额了')
        self.__money = money

    # 私有函数
    # 类的内部可以访问私有函数和私有变量
    def __demo(self):
        print('我是demo函数')


p = Person('张三', 18)
# p.test()
# 获取私有变量的方式
# print(p._Person__money)
print(p.get_money())
p.set_money(1000)
```

```python
class Calculator:
    @staticmethod
    def add(a, b):
        return a + b

    @staticmethod
    def minus(a, b):
        return a - b


print(Calculator.add(1, 2))


class Person(object):
    type = 'human'

    def __init__(self, name, age):
        self.name = name
        self.age = age

    # eat对象方法,可以直接使用实例对象.方法名调用
    def eat(self, food):
        print(self.name + '正在吃' + food)

    # 如果一个方法里没有用到任何实例对象的任何属性(即不需要用到self)，可以将这个方法写成static
    # 静态方法
    @staticmethod
    def demo():
        print('hello')

    # 类方法,如果一个函数只用到了类属性，我们可以把它定义为一个类方法
    @classmethod
    def test(cls):
        # 类方法不需要手动传参，cls指的是类对象Person
        print(cls.type)
        print('yes')


p1 = Person('张三', 18)
p2 = Person('李四', 19)
# 实例对象在调用方法时，不需要给形参self传参，会自动的把实例对象传递给self
p1.eat('红烧牛肉泡面')
print(p1.eat is p2.eat)
print(Person.eat)
# 用类对象来调用对象方法，类对象不会自动传入参数self，需要手动传入参数
Person.eat(p1, '黄焖鸡')
Person.demo()
Person.test()
```

```python
# 	区分对象方法、类方法、静态方法；区分对象属性、类属性
```

```python
# 单例设计模式：只能创建一个实例
class Singleton:
    instance = None

    # 重写__new__方法,需要手动申请内存
    # 类对象和实例对象的地址不一样
    @classmethod
    def __new__(cls, *args, **kwargs):
        if cls.instance is None:
            cls.instance = object.__new__(cls)
        return cls.instance

    def __init__(self, a, b):
        self.a = a
        self.b = b


s1 = Singleton('呵呵', '嘿嘿')
s2 = Singleton('哈哈', '嘻嘻')
print(s1, s2, hex(id(Singleton)))
```

```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def sleep(self):
        print(f'{self.name}正在睡觉')


class Dog(Animal):
    def bark(self):
        print(f'{self.name}正在叫')


class Student(Animal):
    def study(self):
        print(f'{self.name}正在好好学习')


d1 = Dog('大黄', 3)
print(d1.name)
d1.sleep()
d1.bark()
s1 = Student('小明', 18)
s1.sleep()
s1.study()
```

![image-20210320204039221](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210320204039221.png)

```python
class A:  # 如果不写父类，默认继承的父类是object
    def demo_a(self):
        print('我是A类里的方法demo_a')

    def foo(self):
        print('我是A类里的foo')


class B:
    def demo_b(self):
        print('我是A类里的方法demo_b')

    def foo(self):
        print('我是B类的foo')


class C(B, A):
    pass


c = C()
c.demo_a()
c.demo_b()
# 如果两个不同的父类有同名方法，有一个类属性__mro__可以查看方法的调用顺序
# 继承是深度优先而不是广度优先
c.foo()
print(C.__mro__)
```

```python
class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def eat(self):
        print(f'{self.name}正在吃东西')

    def __test(self):
        print('我是Animal类里的test方法')


class Person(Animal):
    pass


p = Person('张三', 18)
print(p.name)
print(p._Person__test())  # 私有属性和私有方法不能继承
```

```python
class Person:
    # __init__也是对象方法
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def sleep(self):
        print(f'{self.name}正在睡觉')


class Student(Person):
    def __init__(self,name,age,school):
        # self.name=name
        # self.age=age
        # 调用父类方法1
        # Person.__init__(self,name,age)
        # 调用父类方法2
        super(Student, self).__init__(name,age)
        self.school=school
    
    def study(self):
        print(f'{self.name}正在学习')

    def sleep(self):  # 重写父类方法
        print(f'{self.name}在课间睡觉')


s = Student('jerry', 20,'春天花花幼稚园')
s.sleep()
```

```python
def can_play(clock):
    print('最外层函数被调用了')

    def handle_action(fn):
        def do_action(name,game):
            if clock<21:
                fn(name,game)
            else:
                print('太晚了')
        return do_action

    return handle_action


# 装饰器函数带参数
@can_play(20)
def play_game(name, game):
    print(name + '正在玩' + game)


play_game('张三', '王者荣耀')
```

```python
# 验证权限使用二进制
# 验证是否有权限用按位与运算
user_permission = 6  # 0b110
read_permission = 4  # 0b100
write_permission = 2  # 0b010
exe_permission = 1  # 0b001


def check_permission(x, y):
    def handle_action(fn):
        def do_action():
            if x & y != 0:
                fn()
            else:
                print('你没有相应的权限')

        return do_action

    return handle_action


@check_permission(user_permission, read_permission)
def read():
    print('我正在读')


@check_permission(user_permission, write_permission)
def write():
    print('我正在写')


@check_permission(user_permission, exe_permission)
def exe():
    print('我正在执行')


read()
write()
exe()
```

```python
# isinstance用来判断一个实例对象是否由指定的类创建出来的
from collections.abc import Iterable


# class Foo:
#     def __next__(self):
#         return 1


class Demo(object):
    def __init__(self, x):
        self.x = x
        self.count = 0

    # 只要重写了__iter__方法就是可迭代对象了
    def __iter__(self):
        return self

    def __next__(self):
        self.count += 1
        if self.count <= self.x:
            return self.count
        else:
            raise StopIteration  # 让迭代器停止


# for...in 循环的本质就是调用对象的__iter__方法,获取这个方法的返回值
# 这个返回值是一个对象，然后再调用这个对象的__next__方法

d = Demo(10)
print(isinstance(d, Iterable))

for i in d:
    print(i)
```

![image-20210329094818901](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210329094818901.png)

![image-20210329094845286](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210329094845286.png)

![image-20210329113116885](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210329113116885.png)

ping出百度的服务器ip地址

![image-20210329113636921](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210329113636921.png)

端口号匹配相应的程序。

![image-20210406101247023](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210406101247023.png)