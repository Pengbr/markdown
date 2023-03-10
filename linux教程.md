# linux教程

Linux 是一种自由和开放源码的类 UNIX 操作系统。

Linux 是在 1991 由林纳斯·托瓦兹在赫尔辛基大学上学时创立的，主要受到 Minix 和 Unix 思想的启发。

# linux简介

目前国内 Linux 更多的是应用于服务器上，而桌面操作系统更多使用的是 Windows。

简单的说，sudo是一种权限管理机制，管理员可以授权于一些普通用户去执行一些root执行的操作，而不需要知道root的密码。严谨的说，sudo允许一个已授权用户以超级用户或者其它用户的角色运行一个命令。

# Linux 系统启动过程

```sh
reboot 就是重启，等同于 shutdown –r now
```

```shell
halt 关闭系统，等同于shutdown –h now 和 poweroff
```

要取消即将进行的关机，只要输入下面的命令：

```shell
# shutdown -c
```

# Linux 系统目录结构

**/sbin**：
s 就是 Super User 的意思，是 Superuser Binaries (超级用户的二进制文件) 的缩写，这里存放的是系统管理员使用的系统管理程序。

如果一个目录或文件名以一个点 . 开始，表示这个目录或文件是一个隐藏目录或文件(如：.bashrc)。即以默认方式查找时，不显示该目录或文件。

**/usr**：用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录。

# Linux 远程登录

Linux 一般作为服务器使用，而服务器一般放在机房，你不可能在机房操作你的 Linux 服务器。

这时我们就需要远程登录到Linux服务器来管理维护系统。

Linux 系统中是通过 ssh 服务实现的远程登录功能，默认 ssh 服务端口号为 22。

Window 系统上 Linux 远程登录客户端有 SecureCRT, Putty, SSH Secure Shell 等

# Linux 文件基本属性

![image-20210125205849805](C:\Users\HP1\AppData\Roaming\Typora\typora-user-images\image-20210125205849805.png)

### chgrp：更改文件属组

```shell
chgrp [-R] 属组名 文件名
```

-R：递归更改文件属组，就是在更改某个目录文件的属组时，如果加上-R的参数，那么该目录下的所有文件的属组都会更改。

# Linux 文件与目录管理

pwd（英文全拼：print work directory）：显示目前的目录

你可以使用 *man [命令]* 来查看各个命令的使用文档，如 ：man cp。

### ls (列出目录)

- -a ：全部的文件，连同隐藏文件( 开头为 . 的文件) 一起列出来(常用)
- -d ：仅列出目录本身，而不是列出目录内的文件数据(常用)
- -l ：长数据串列出，包含文件的属性与权限等等数据；(常用)

将家目录下的所有文件列出来(含属性与隐藏档)

```shell
[root@www ~]# ls -al ~
```

### rm (移除文件或目录)

- -f ：就是 force 的意思，忽略不存在的文件，不会出现警告信息；
- -i ：互动模式，在删除前会询问使用者是否动作
- -r ：递归删除啊！最常用在目录的删除了！这是非常危险的选项！！！

## Linux 文件内容查看

Linux系统中使用以下命令来查看文件的内容：

- cat 由第一行开始显示文件内容
- tac 从最后一行开始显示，可以看出 tac 是 cat 的倒着写！
- nl  显示的时候，顺道输出行号！
- more 一页一页的显示文件内容
- less 与 more 类似，但是比 more 更好的是，他可以往前翻页！
- head 只看头几行
- tail 只看尾巴几行

/字串     ：代表在这个显示的内容当中，向下搜寻『字串』这个关键字；(more、less)

# Linux 用户和用户组管理

```shell
口令：passwd 即代表密码
```

# Linux 磁盘管理

Linux磁盘管理好坏直接关系到整个系统的性能问题。

Linux磁盘管理常用三个命令为df、du和fdisk。

- df：列出文件系统的整体磁盘使用量
- du：检查磁盘空间使用量
- fdisk：用于磁盘分区

# Linux vi/vim

基本上 vi/vim 共分为三种模式，分别是**命令模式（Command mode）**，**输入模式（Insert mode）**和**底线命令模式（Last line mode）**。

### 输入模式

- **HOME**/**END**，移动光标到行首/行尾

- **Page Up**/**Page Down**，上/下翻页

![image-20210129183714853](C:\Users\HP1\AppData\Roaming\Typora\typora-user-images\image-20210129183714853.png)

# Linux yum 命令

- \1. 列出所有可更新的软件清单命令：**yum check-update**
- \2. 更新所有软件命令：**yum update**
- \3. 仅安装指定的软件命令：**yum install <package_name>**
- \4. 仅更新指定的软件命令：**yum update <package_name>**
- \5. 列出所有可安裝的软件清单命令：**yum list**
- \6. 删除软件包命令：**yum remove <package_name>**
- \7. 查找软件包命令：**yum search <keyword>**

# Linux apt 命令

# linux nano/gedit/vim

# Shell 教程

*#!/bin/bash*
**echo** "Hello World !"

**#!** 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即使用哪一种 Shell。

# Shell 变量

使用一个定义过的变量，只要在变量名前面加美元符号即可，如：

```shell
your_name="qinjx"
echo $your_name
echo ${your_name}
```

### 只读变量

使用 readonly 命令可以将变量定义为只读变量，只读变量的值不能被改变。

下面的例子尝试更改只读变量，结果报错：

```shell
#!/bin/bash
myUrl="https://www.google.com"
readonly myUrl
myUrl="https://www.runoob.com"
```

运行脚本，结果如下：

```shell
/bin/sh: NAME: This variable is read only.
```

### 删除变量

使用 unset 命令可以删除变量。

```shell
#!/bin/sh
myUrl="https://www.runoob.com"
unset myUrl
echo $myUrl
```

单引号里的任何字符都会原样输出，单引号字符串中的变量是无效的；

### 多行注释

```shell
:<<EOF
注释内容...
注释内容...
注释内容...
EOF
```

# Shell 传递参数

./加上可执行文件的名字执行文件

# Shell printf 命令

```shell
$ **echo** "Hello, Shell"
Hello, Shell
$ **printf** "Hello, Shell**\n**"
Hello, Shell
$
```

printf不像echo自动添加换行符，需要手动添加\n

printf有格式化字符串的功能

# Shell test 命令

Shell中的 test 命令用于检查某个条件是否成立，它可以进行数值、字符和文件三个方面的测试。

# Shell 流程控制

## if else

```shell
a=10
b=20
**if** **[** $a == $b **]**
**then**
  **echo** "a 等于 b"
**elif** **[** $a -gt $b **]**
**then**
  **echo** "a 大于 b"
**elif** **[** $a -lt $b **]**
**then**
  **echo** "a 小于 b"
**else**
  **echo** "没有符合的条件"
**fi**
```

## for 循环

```shell
for var in item1 item2 ... itemN
do
    command1
    command2
    ...
    commandN
done
```

## while 语句

```shell
while condition
do
    command
done
```

## case ... esac

**case ... esac** 为多选择语句，与其他语言中的 switch ... case 语句类似，是一种多分枝选择结构

```shell
case 值 in
模式1)
    command1
    command2
    ...
    commandN
    ;;
模式2）
    command1
    command2
    ...
    commandN
    ;;
esac
```

# Shell 函数

在Shell中，调用函数时可以向其传递参数。在函数体内部，通过 $n 的形式来获取参数的值，例如，$1表示第一个参数，$2表示第二个参数...

# Shell 输入/输出重定向

| command > file  | 将输出重定向到 file。             |
| --------------- | --------------------------------- |
| command >> file | 将输出以追加的方式重定向到 file。 |

```shell
$ who > users
```

```shell
$ cat users
_mbsetupuser console  Oct 31 17:35 
tianqixin    console  Oct 31 17:35 
tianqixin    ttys000  Dec  1 11:33 
```

注意：输出重定向是大于号(>)，输入重定向是小于号(<)。

# Nginx 安装配置

Nginx("engine x")

# MySQL 安装配置



# 其它

EOF可以代表一个运行环境

docker类似一个一个的胶囊房

Ubuntu专为中国打造的发行版之一kylin(优麒麟)系统

shell进行数学运算时需要使用expr命令，同时注意数字与运算符号之间要有空格隔开。

管道符 | 从前往后传，如果需要对linux命令的输出结果进行再次处理，就可以使用管道符+管道命令解决

**常用命令总结：**

cut、paste、ls、cd、more、touch、cat、vi/vim、gedit、tail、chmod、apt、echo、sed、awk、grep、rm、find、mv、cp、man...

wc -l显示列数

mkdir -p递归创建目录

tcsh是csh的增强版

```shell
# 常用指令
ps 显示所有进程信息
ps -ef 
```



# linux三剑客sed、awk、grep

三剑客的功能非常强大，但我们只需要掌握他们分别擅长的领域即可：**grep擅长查找功能，sed擅长取行和替换。awk擅长取列。**

grep基础正则，egrep扩展正则

sed命令：增删改查

sed查找：p    sed删除: d   sed增加：cai   sed替换：s

awk中内置变量：NR代表行号，NF代表列号

awk中-F指定分隔符
