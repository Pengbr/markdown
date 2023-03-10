# Go 语言教程

## 第一个 Go 程序

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

可以使用go run来执行程序，也可使用go build命令将源代码编译成二进制可执行文件。

go语言编译器会在语句结束时自动添加分号。

可执行的文件才能引入main包，main函数只能位于main包中。

go get 安装包

![image-20220911155656795](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20220911155656795.png)

# Go 语言环境安装

# Go 语言结构

*func main()* 是程序开始执行的函数。main 函数是每一个可执行程序所必须包含的，一般来说都是在启动后第一个执行的函数（如果有 init() 函数则会先执行该函数）

单行注释是最常见的注释形式，你可以在任何地方使用以 // 开头的单行注释。多行注释也叫块注释，均已以 /* 开头，并以 */ 结尾，且不可以嵌套使用，多行注释一般用于包的文档描述或注释成块的代码片段。

*fmt.Println(...)* 可以将字符串输出到控制台，并在最后自动增加换行字符 \n。
使用 fmt.Print("hello, world\n") 可以得到相同的结果。
Print 和 Println 这两个函数也支持使用变量，如：fmt.Println(arr)。如果没有特别指定，它们会以默认的打印格式将变量 arr 输出到控制台。

# Go 语言基础语法

## 标识符

标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

## 格式化字符串

Go 语言中使用 **fmt.Sprintf** 格式化字符串并赋值给新串：

```go
package main

import (
    "fmt"
)

func main() {
   // %d 表示整型数字，%s 表示字符串
    var stockcode=123
    var enddate="2020-12-31"
    var url="Code=%d&endDate=%s"
    var target_url=fmt.Sprintf(url,stockcode,enddate)
    fmt.Println(target_url)
}
```

# Go 语言数据类型

字符串、数值、布尔、派生类型

# Go 语言变量

零值就是变量没有做初始化时系统默认设置的值。

```go
package main
import "fmt"
func main() {

    // 声明一个变量并初始化
    var a = "RUNOOB"
    fmt.Println(a)

    // 没有初始化就为零值
    var b int
    fmt.Println(b)

    // bool 零值为 false
    var c bool
    fmt.Println(c)
}
```

以上实例执行结果为：

```go
RUNOOB
0
false
```

我们知道可以在变量的初始化时省略变量的类型而由系统自动推断，声明语句写上 var 关键字其实是显得有些多余了，因此我们可以将它们简写为 a := 50 或 b := false。

a 和 b 的类型（int 和 bool）将由编译器自动推断。

**这是使用变量的首选形式，但是它只能被用在函数体内，而不可以用于全局变量的声明与赋值。**使用操作符 := 可以高效地创建一个新的变量，称之为初始化声明。

# Go 语言常量

```go
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5  
   var area int
   const a, b, c = 1, false, "str" //多重赋值

   area = LENGTH * WIDTH
   fmt.Printf("面积为 : %d", area)
   println()
   println(a, b, c)  
}
```

## iota

iota，特殊常量，可以认为是一个可以被编译器修改的常量。

iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。

### iota 用法

```go
package main

import "fmt"

func main() {
    const (
            a = iota   //0
            b          //1
            c          //2
            d = "ha"   //独立值，iota += 1
            e          //"ha"   iota += 1
            f = 100    //iota +=1
            g          //100  iota +=1
            h = iota   //7,恢复计数
            i          //8
    )
    fmt.Println(a,b,c,d,e,f,g,h,i)
}
```

以上实例运行结果为：

```go
0 1 2 ha ha 100 100 7 8
```

# Go 语言运算符

go语言支持自增自减运算符，自增++，自减--

## 逻辑运算符

| 运算符 |                             描述                             |        实例        |
| :----: | :----------------------------------------------------------: | :----------------: |
|   &&   | 逻辑 AND 运算符。 如果两边的操作数都是 True，则条件 True，否则为 False。 | (A && B) 为 False  |
|  \|\|  | 逻辑 OR 运算符。 如果两边的操作数有一个 True，则条件 True，否则为 False。 | (A \|\| B) 为 True |
|   !    | 逻辑 NOT 运算符。 如果条件为 True，则逻辑 NOT 条件 False，否则为 True。 | !(A && B) 为 True  |

# Go 语言条件语句

![image-20210307143212569](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210307143212569.png)

Go 语言提供了以下几种条件判断语句：

|                             语句                             |                             描述                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|  [if 语句](https://www.runoob.com/go/go-if-statement.html)   |    **if 语句** 由一个布尔表达式后紧跟一个或多个语句组成。    |
| [if...else 语句](https://www.runoob.com/go/go-if-else-statement.html) | **if 语句** 后可以使用可选的 **else 语句**, else 语句中的表达式在布尔表达式为 false 时执行。 |
| [if 嵌套语句](https://www.runoob.com/go/go-nested-if-statements.html) | 你可以在 **if** 或 **else if** 语句中嵌入一个或多个 **if** 或 **else if** 语句。 |
| [switch 语句](https://www.runoob.com/go/go-switch-statement.html) |        **switch** 语句用于基于不同条件执行不同动作。         |
| [select 语句](https://www.runoob.com/go/go-select-statement.html) | **select** 语句类似于 **switch** 语句，但是select会随机执行一个可运行的case。如果没有case可运行，它将阻塞，直到有case可运行。 |

## Go 语言 if 语句

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var a int = 10
 
   /* 使用 if 语句判断布尔表达式 */
   if a < 20 {
       /* 如果条件为 true 则执行以下语句 */
       fmt.Printf("a 小于 20\n" )
   }
   fmt.Printf("a 的值为 : %d\n", a)
}
```

## Go 语言 if...else 语句

```go
package main

import "fmt"

func main() {
   /* 局部变量定义 */
   var a int = 100;
 
   /* 判断布尔表达式 */
   if a < 20 {
       /* 如果条件为 true 则执行以下语句 */
       fmt.Printf("a 小于 20\n" );
   } else {
       /* 如果条件为 false 则执行以下语句 */
       fmt.Printf("a 不小于 20\n" );
   }
   fmt.Printf("a 的值为 : %d\n", a);

}
```

## Go 语言 if 语句嵌套

你可以在 if 或 else if 语句中嵌入一个或多个 if 或 else if 语句。

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var a int = 100
   var b int = 200
 
   /* 判断条件 */
   if a == 100 {
       /* if 条件语句为 true 执行 */
       if b == 200 {
          /* if 条件语句为 true 执行 */
          fmt.Printf("a 的值为 100 ， b 的值为 200\n" );
       }
   }
   fmt.Printf("a 值为 : %d\n", a );
   fmt.Printf("b 值为 : %d\n", b );
}
```

## Go 语言 switch 语句

switch 语句用于基于不同条件执行不同动作，每一个 case 分支都是唯一的，从上至下逐一测试，直到匹配为止。

switch 语句执行的过程从上至下，直到找到匹配项，匹配项后面也不需要再加 break。

switch 默认情况下 case 最后自带 break 语句，匹配成功后就不会执行其他 case，如果我们需要执行后面的 case，可以使用 **fallthrough** 。

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var grade string = "B"
   var marks int = 90

   switch marks {
      case 90: grade = "A"
      case 80: grade = "B"
      case 50,60,70 : grade = "C"
      default: grade = "D"  
   }

   switch {
      case grade == "A" :
         fmt.Printf("优秀!\n" )    
      case grade == "B", grade == "C" :
         fmt.Printf("良好\n" )      
      case grade == "D" :
         fmt.Printf("及格\n" )      
      case grade == "F":
         fmt.Printf("不及格\n" )
      default:
         fmt.Printf("差\n" );
   }
   fmt.Printf("你的等级是 %s\n", grade );      
}
```

# Go 语言循环语句

## Go 语言 for 循环

### 实例

```go
package main

import "fmt"

func main() {
        sum := 0
        for i := 0; i <= 10; i++ {
                sum += i
        }
        fmt.Println(sum)
}
```

```go
package main

import "fmt"

func main() {
        sum := 1
        for ; sum <= 10; {
                sum += sum
        }
        fmt.Println(sum)

        // 这样写也可以，更像 While 语句形式
        for sum <= 10{
                sum += sum
        }
        fmt.Println(sum)
}
```

## Go 语言 goto 语句

在变量 a 等于 15 的时候跳过本次循环并回到循环的开始语句 LOOP 处：

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var a int = 10

   /* 循环 */
   LOOP: for a < 20 {
      if a == 15 {
         /* 跳过迭代 */
         a = a + 1
         goto LOOP
      }
      fmt.Printf("a的值为 : %d\n", a)
      a++    
   }  
}
```

# Go 语言函数

## 函数定义

Go 语言函数定义格式如下：

```go
func function_name( [parameter list] ) [return_types] {
   函数体
}
```

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var a int = 100
   var b int = 200
   var ret int

   /* 调用函数并返回最大值 */
   ret = max(a, b)

   fmt.Printf( "最大值是 : %d\n", ret )
}

/* 函数返回两个数的最大值 */
func max(num1, num2 int) int {
   /* 定义局部变量 */
   var result int

   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result
}
```

## 函数返回多个值

Go 函数可以返回多个值，例如：

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
   return y, x
}

func main() {
   a, b := swap("Google", "Runoob")
   fmt.Println(a, b)
}
```

## Go 语言函数作为实参

将函数当作一个变量

```go
package main

import (
   "fmt"
   "math"
)

func main(){
   /* 声明函数变量 */
   getSquareRoot := func(x float64) float64 {
      return math.Sqrt(x)
   }

   /* 使用函数 */
   fmt.Println(getSquareRoot(9))

}
```

# Go 语言变量作用域

作用域为已声明标识符所表示的常量、类型、变量、函数或包在源代码中的作用范围。

Go 语言中变量可以在三个地方声明：

- 函数内定义的变量称为局部变量
- 函数外定义的变量称为全局变量
- 函数定义中的变量称为形式参数

# Go 语言数组

## 声明数组

Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

```go
var variable_name [SIZE] variable_type
// 以上为一维数组的定义方式。例如以下定义了数组 balance 长度为 10 类型为 float32：
var balance [10] float32
```

如果数组长度不确定，可以使用 **...** 代替数组的长度，编译器会根据元素个数自行推断数组的长度：

```go
var balance = [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
或
balance := [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
```

# Go 语言指针

Go 语言的取地址符是 &，放到一个变量前使用就会返回相应变量的内存地址。

```go
package main

import "fmt"

func main() {
   var a int = 10  

   fmt.Printf("变量的地址: %x\n", &a  )
}
```

```go
package main

import "fmt"

func main() {
   var a int= 20   /* 声明实际变量 */
   var ip *int        /* 声明指针变量 */

   ip = &a  /* 指针变量的存储地址 */

   fmt.Printf("a 变量的地址是: %x\n", &a  )

   /* 指针变量的存储地址 */
   fmt.Printf("ip 变量储存的指针地址: %x\n", ip )

   /* 使用指针访问值 */
   fmt.Printf("*ip 变量的值: %d\n", *ip )
}
```

# Go 语言结构体

Go 语言中数组可以存储同一类型的数据，但在结构体中我们可以为不同项定义不同的数据类型。

结构体是由一系列具有相同类型或不同类型的数据构成的数据集合。

# Go语言方法

属性和方法分开。结构体中描述属性，函数将结构体作为接收者充当方法

# Go语言接口

通过接口实现多态

```go
package main

import (
	"fmt"
)

type USB interface {
	read()
	write()
}

type Computer struct {
	name string
}

type Mobile struct {
	name string
}

func (c Computer) read() {
	fmt.Println(c.name)
	fmt.Println("read")
}

func (c Computer) write() {
	fmt.Println(c.name)
	fmt.Println("write")
}

func (m Mobile) read() {
	fmt.Println("iphone read")
}

func (m Mobile) write() {
	fmt.Println("iphone write")
}

func main() {
	c := Computer{
		name: "hp",
	}
	c.read()
	c.write()

	// 通过接口实现多态
	var usb USB
	usb = Computer{
		name: "lianxiang",
	}
	usb.read()

	usb = Mobile{
		name: "iphone",
	}
	usb.read()
}
```

## ocp原则

开闭原则。对扩展是开放的，对修改是关闭的

# Go语言包

go mod包管理工具

# Go语言注意事项

整数回绕问题

常量的值会在编译的时候确定，函数调用发生在运行时，所以不能将函数的返回值赋值给常量。

## new与make的区别

区别：在go语言中，make和new都是内存的分配（堆上），但是make只用于slice、map以及channel的初始化（非零值）；而new用于类型的内存分配，并且内存置为零。make返回的是引用类型本身；而new返回的是指向类型的指针。

# Go语言并发

go语言的并发是通过协程实现的

通道：缓冲通道、定向通道        协程之间通过通道进行通信

无缓冲通道只能同步通信，有缓冲通道可以异步通信

通道不用make分配空间的话默认为nil

```go
package main

import "fmt"

var c = make(chan int)

func main() {
	go func() {
		for i := 0; i < 10; i++ {
			c <- i
		}
		close(c)
	}()

	for v := range c {
		fmt.Println(v)
	}
}
```

通过waitGroup实现同步，增加一个任务就加1，完成一个任务就减1，wait()函数等待，add()加一，done()减一

使用waitGroup就不用使用time.sleep了，提高程序的运行效率（主协程等待子协程运行完毕）

```go
func main() {
    wg := sync.WaitGroup{}
    wg.Add(100)
    for i := 0; i < 100; i++ {
        go func(i int) {
            fmt.Println(i)
            wg.Done()
        }(i)
    }
    wg.Wait()
}
```

runtime包

mutex互斥锁（当用多个线程同时访问修改公共数据时，需要上锁，防止获得脏数据）

```go
package main

import (
	"fmt"
	"sync"
)

var i int = 100
var wg sync.WaitGroup
var lock sync.Mutex

func add() {
	defer wg.Done()
	lock.Lock()
	i += 1
	fmt.Println("i++", i)
	lock.Unlock()
}

func sub() {
	defer wg.Done()
	lock.Lock()
	i -= 1
	fmt.Println("i--", i)
	lock.Unlock()
}

func main() {
	for j := 0; j < 100; j++ {
		wg.Add(1)
		go add()
		wg.Add(1)
		go sub()
	}
	wg.Wait()
	fmt.Println("end i", i)
}
```

select语句

```go
package main

import (
	"fmt"
	"time"
)

var chanInt = make(chan int, 0)
var chanStr = make(chan string)

func main() {
	go func() {
		chanInt <- 100
		chanStr <- "hello"
		defer close(chanInt)
		defer close(chanStr)
	}()

	for {
		select {
		case r := <-chanInt:
			fmt.Println(r)
		case r := <-chanStr:
			fmt.Println(r)
		default:
			fmt.Println("default...")
		}
		time.Sleep(time.Second)
	}
}
```

go原子操作   CAS

```go
// 原子操作也能保证线程安全
package main

import (
	"fmt"
	"sync/atomic"
	"time"
)

var j int32 = 100

func add1() {
	atomic.AddInt32(&j, 1)
}

func reduce() {
	atomic.AddInt32(&j, -1)
}

func main() {
	for i := 0; i < 100; i++ {
		go add1()
		go reduce()
	}

	time.Sleep(time.Second * 3)
	fmt.Println(j)
}
```

CAS机制

它的英文全称是 Compare-And-Swap，中文叫做“比较并交换”，它是一种思想、一种算法

在多线程的情况下，各个代码的执行顺序是不能确定的，所以为了保证并发安全，我们可以使用互斥锁。而 CAS 的特点是避免使用互斥锁，当多个线程同时使用 CAS 更新同一个变量时，只有其中一个线程能够操作成功，而其他线程都会更新失败。不过和同步互斥锁不同的是，更新失败的线程并不会被阻塞，而是被告知这次由于竞争而导致的操作失败，但还可以再次尝试

CAS 被广泛应用在并发编程领域中，以实现那些不会被打断的数据交换操作，从而就实现了无锁的线程安全

在大多数处理器的指令中，都会实现 CAS 相关的指令，这一条指令就可以完成“比较并交换”的操作，也正是由于这是一条（而不是多条）CPU 指令，所以 CAS 相关的指令是具备原子性的，这个组合操作在执行期间不会被打断，这样就能保证并发安全。由于这个原子性是由 CPU 保证的，所以无需程序员来操心

> CAS 有三个操作数：内存值 V、预期值 A、要修改的值 B。CAS 最核心的思路就是，**仅当预期值 A 和当前的内存值 V 相同时，才将内存值修改为 B**

```go
package main

import (
	"fmt"
	"sync/atomic"
)

func main() {
	var i int32 = 100
	b := atomic.CompareAndSwapInt32(&i, 100, 200)
	fmt.Println(b)
	fmt.Println(i)
}
```



# go操作mysql

安装配置mysql驱动

> installation

```go
$ go get -u github.com/go-sql-driver/mysql
```



# Go学习路线

1、学习go数据结构与算法，刷Leecode

2、做go项目，包括微服务、web、分布式等等

3、计算机基础知识的学习，包括编译原理、汇编语言、mysql原理与性能优化、大数据分布式等等

# 其它

将go作为我的主力语言，node、python主要当做工具、辅助语言来使用

基本数据类型与复合数据类型

数组为复合数据类型，数据类型的形式为：[4]int

go语言数组是定长的，slice切片可以看做是变长数组，可以使用make函数创建切片 [ ]int      make([ ]int,3,8)

深拷贝：拷贝的是数据本身；浅拷贝：拷贝的是数据地址

go语言可变参数三个点写在参数后面与js相反，装包与拆包

defer栈结构，先被defer的后执行

go语言结构体类似其它语言的类

go语言中make函数用于引用类型初始化的，new函数用于创建值类型的指针

go语言中同时有函数和方法。一个方法就是一个包含了接受者的函数，接受者可以是命名类型或者结构体类型的一个值或者是一个指针

方法是某个类别的行为功能，需要指定的接受者调用

接口是一组方法的定义，具体方法的实现是实现接口

go语言错误与异常，错误err，异常panic

go语言init()函数，main()函数

go导包导的是一个文件夹，python导包导的是一个文件，go导包要设置gopath

反射操作：通过反射，可以获取一个接口类型变量的类型和数值

go与c语言、Fortran类似，src文件夹是存放源码的，bin文件夹是存放编译后的二进制文件。pkg文件夹是go用来存放包的

go中每个接口都有一些方法，只要结构体实现了这些方法，那么这些结构体就是这个接口类型

**函数里面传递引用类型外面也能收到**，不受函数作用域的影响

读并发是安全的，写并发是不安全的需要加锁

同一个包下的函数可以相互调用
