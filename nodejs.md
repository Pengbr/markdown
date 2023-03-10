nodejs不能解释、不需要解释webAPI

文件的写入与打开

文件下载要通过流的形式

axios库、cheerio库、puppeteer库 

域名解析得到IP地址

ipv4不够用后出现了ipv6

cookie可以看到用户是否登录过，从而给用户返回不同的界面

nodejs类似浏览器，是JS的一个运行环境

按住shift加上右键看到打开终端的命令

以（  [   `开头的前面加上；

art-template模板引擎

**nvm---nodejs版本管理工具**

**nvm下载nodejs  nvm install 10.15.0     切换版本  nvm use  v12.16.2    查看版本 nvm list**

nodejs中的全局对象是**global**,不是window     

**主入口文件**：所围主入口文件，就是程序项目或者系统被访问请求的时候，第一个被访问到的文件，所有的指令功能都是从这文件分发出去，再找相对应的模块进行处理，一些初始化的工作也在这里进行，这个文件可以根据不同的请求去调用框架不同的模块，这里甚至可以设定一些参数，方便以后的开发和维护。

get请求：查询用的，有查询字符串

模块化路由，注册路由模块

标记删除



## path模块

```javascript
// 引入path模块，path应该是一个对象,path模块用来处理与路径相关的事情
const path = require('path')

// 得到当前执行文件的绝对路径，不包括文件名
console.log(__dirname)
// 绝对路径包括文件名
console.log(__filename)

// 获取扩展名
let extname = path.extname(__filename)
// 获取文件名，包括扩展名
let basename = path.basename(__filename)
// 获取指定文件所在路径
let dirname = path.dirname(__filename)
console.log(extname, basename, dirname)

// parse路径解析,将路径解析为对象
let parseObj = path.parse(__filename)
console.log(parseObj)


// 拼接操作
let fullPath = path.join(__dirname, 'path内置模块.js')
console.log(fullPath)
```



buffer数据类型，二进制数据类型

```javascript
fs.readFile(filePath, 'utf-8', (error, data) => {
    // console.log(error, data) // error是错误信息，没发生错误为null,data是读取到的内容
    // 出现错误时data就是undefined
    if (error) return error // 思路：不对就return掉，避免往下执行
    console.log(data)
})
```



## 回调地狱

```javascript
const fs = require('fs')
const path = require('path')

let pathName1 = path.join(__dirname, 'file', '1.txt')
let pathName2 = path.join(__dirname, 'file', '2.txt')
let pathName3 = path.join(__dirname, 'file', '3.txt')
let pathName4 = path.join(__dirname, 'file', 'data.txt')


// 方法是异步的，要保证顺序读取，就会出现回调地狱
fs.readFile(pathName1, 'utf-8', (error1, data1) => {
    if (error1) {
        console.log(error1)
        return
    }
    // 读取完第一个文件数据后继续读取第二个文件的数据
    fs.readFile(pathName2, 'utf-8', (error2, data2) => {
        if (error2) {
            console.log(error2)
            return
        }
        fs.readFile(pathName3, 'utf-8', (error3, data3) => {
            if (error3) {
                console.log(error3)
                return
            }
            console.log(data1 + data2 + data3)
            let result = data1 + data2 + data3
            // 写入文件
            fs.writeFile(pathName4, result, 'utf-8', (error4) => {
                if (error4) {
                    console.log(error4)
                    return
                }
                console.log('写完了')
            })
        })
    })
})
```



get请求如打开某个页面；post请求如登录某个页面，因为要传入信息给后端，当传入信息给后端时为post请求。

yarn包管理工具       yarn  add  包名

nodejs不支持es6的模块化规范



## promise

```javascript
const fs = require('fs')
const path = require('path')

let filePath1 = path.join(__dirname, 'file', '1.txt')

let p1 = new Promise((resolve, reject) => {
    // resolve,reject都是函数
    fs.readFile(filePath1, 'utf-8', ((err, data) => {
        if (err) {
            reject(err)
        }
        resolve(data)  // 调用的是p1.then的第一个函数
    }))
})

// then方法传入了两个函数,then方法可以链式调用
// then的函数里可以有返回值，被下一个then的形参接受
// 如果返回的是一个promise对象，下一个then的形参接受到的不是promise对象，而是这个promise对象内部的resolve函数的参数
p1.then((data) => {
    console.log('成功了')
    console.log(data)
    return p1
}, (err) => {
    console.log('失败了')
    console.log(err)
}).then((data) => {
    // 不管第一个成功与否，第二个then都会执行
    console.log('第二个then', data)
    return '222'
}).then((data) => {
    console.log('第三个then', data)
})
```



## 请求报文与响应报文

请求行的信息：get   /  HTTP/1.1    get请求；/ 根路径；HTTP/1.1协议版本  

请求行、请求头、空行、请求体     get请求没有请求体，post请求有请求体

请求头都是一些键值对

操作系统自动给浏览器分配端口号

响应行的信息： HTTP/1.1  200 OK    协议版本；响应状态码

响应头、空行、响应体，响应头同样也都是键值对，响应体就是html中的内容

tcp三次握手与四次挥手



## 跨域

协议、域名、端口不一样就可能出现跨域。

跨域，服务器不能去处理别的网站的js代码。协议、域名、端口有一个不一样都称为别的网站。

解决跨域问题jsonp、cors（主流的解决方案）

cors跨域资源共享

浏览器的**同源安全策略**默认会阻止网页跨域获取资源。但如果接口服务器配置了CORS相关的HTTP响应头，就可以解除浏览器端的跨域访问限制。

简单请求与预检请求



## cookie与session

视图、路由、入口文件、静态文件

钩子函数、动态路由、模板过滤器、模板继承

http是一种无状态协议，实现状态保持主要有两种方式：在客户端存储信息使用cookie，在服务器端存储信息使用session

cookie特点： 1、cookie有服务器生成，保存在浏览器端的一小段文本信息

​                      2、cookie是以键和值的形式进行存储

​                      3、浏览器在访问一个网站服务时，会自动在请求头中把和本网站相关的所有cookie发送给服务器

​                      4、cookie是基于域名安全的

​                      5、cookie有过期时间，默认关闭浏览器之后过期

cookie与session



## 数据库

mysql -uroot -p   进入mysql数据库

show databases; 展示数据库

show tables 展示表

关系型数据库（表和表之间是有关系的）和非关系型数据库

使用Navicat客户端操作数据库

对于图片、音频、视频等文件，不存储在数据库中，而是上传到某个服务器上，然后在表中存储这个文件的保存路径

数据约束，用来约束字段，主键、非空、惟一、默认、外键

删除数据库  drop database 数据库名

desc 表名    查询表结构

插入数据 insert into

修改数据 update

删除数据 delete

模糊查询  like            %通配符             范围查询 in、between...and         排序查询  order by       聚合函数 count()、max()、min()、sum()、avg()、round()          

分组查询  group by      group_concat()组内合并            **查询条件：where；分组条件：having**（聚合函数如果作为条件出现，只能与having配合，having与group by连用）

分页查询 limit   （先排序再分页）

连接查询 inner join       on 当...时候

子查询：一个查询的结果作为另一个查询的一部分

mysql workbench类似Navicat           workbench工作台



## 后台服务器获取数据库数据

orm对象---关系映射

把数据库每一条记录映射为对象，字段映射为属性（用面向对象的方法操作数据库）

orm框架

**node会默认到node_modules文件夹下找模块，在没有其它配置的情况下，自己定义的模块也要放到node_modules文件夹下**

orm框架中模型（model）就是代表的表



## csrf跨站请求伪造

form表单中submit会触发form中的action

用户c在登录网站a之后，没有退出的情况下，访问了第三方网站，第三方网站可能以用户c的身份去向服务器a发起请求

网站b伪造成用户c的身份，使用了网站a的一些功能

浏览器同源策略防止跨域

在执行router下接口之前执行钩子函数中的代码，通过钩子函数来做csrf跨站请求伪造的防护



## 中间件

客服端请求——>中间件——>中间件或路由——>服务器响应给客服端

middleware

```js
// 路由处理函数
app.get('/',(req,res,next)=>{
    next()
})
```

中间件分类

应用中间件、路由中间件

错误级别的中间件 (err,req,res,next)

express内置中间件

第三方的中间件

中间件共享同一份req和res



## 身份认证

cookie与session   jwt认证机制

jwt token



## 项目

```js
// 注意如果不是直接引入的node_modules中的js文件需要添加./
const appConfig = require('./config')
```

一个项目一个数据库有多个数据表，如收藏表、用户表、关注表、粉丝表等等，并且各个表之间相互关联。

![image-20210821111609896](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210821111609896.png)

navicat可以运行sql文件

captcha验证码

接口与路由

nodemon是一种工具，可以自动检测到目录中的文件更改时通过重新启动应用程序来调试基于node.js的应用程序。（热更新）

云开发（CloudBase）是云端一体化的后端云服务 ，采用 serverless 架构，免去了移动应用构建中繁琐的服务器搭建和运维。同时云开发提供的静态托管、命令行工具（CLI）、Flutter SDK 等能力降低了应用开发的门槛。使用云开发可以构建完整的小程序/小游戏、H5、Web、移动 App 等应用。

图片验证码模块：svg-captcha

前端的数据不安全，后端必须做严格的数据处理

session与cookie状态保持    有点像vue中的vuex



## others

events 模块只提供了一个对象： events.EventEmitter。EventEmitter 的核心就是事件触发与事件监听器功能的封装。

使用nw.js可以打包成exe可执行程序（轻量级桌面应用）

使用nginx部署静态文件  动静分离

**后端向前端请求数据req（接收来自前端的数据），后端向前端响应数据res，前端向后端请求数据可以用axios框架**

**get请求数据来自服务器，post请求是向服务器传送数据**

图片压缩库images特别好用 :smile:，还有sharp、gm图像处理库等等

**i5ting_toc可以快速地将md文件转为html文件**

**i5ting_toc -f xxx.md -o**

npm login       npm publish发布包    npm unpublish删除已发布的包

### 管道流

管道提供了一个输出流到输入流的机制。通常我们用于从一个流中获取数据并将数据传递到另外一个流中。

以下实例我们通过读取一个文件内容并将内容写入到另外一个文件中。

```javascript
var fs = require("fs");

// 创建一个可读流
var readerStream = fs.createReadStream('input.txt');

// 创建一个可写流
var writerStream = fs.createWriteStream('output.txt');

// 管道读写操作
// 读取 input.txt 文件内容，并将内容写入到 output.txt 文件中
readerStream.pipe(writerStream);

console.log("程序执行完毕");
```

### 链式流

链式是通过连接输出流到另外一个流并创建多个流操作链的机制。链式流一般用于管道操作。

接下来我们就是用管道和链式来压缩和解压文件。

```js
var fs = require("fs");
var zlib = require('zlib');

// 压缩 input.txt 文件为 input.txt.gz
fs.createReadStream('input.txt')
  .pipe(zlib.createGzip())
  .pipe(fs.createWriteStream('input.txt.gz'));
  
console.log("文件压缩完成。");
```

### **exports 和 module.exports 的使用**

如果要对外暴露属性或方法，就用 **exports** 就行，要暴露对象(类似class，包含了很多属性和方法)，就用 **module.exports**。

### Telnet

Telnet协议是[TCP/IP协议](https://baike.baidu.com/item/TCP%2FIP协议)族中的一员，是Internet远程登录服务的标准协议和主要方式。它为用户提供了在本地计算机上完成远程[主机](https://baike.baidu.com/item/主机/455151)工作的能力。在[终端](https://baike.baidu.com/item/终端/1903878)使用者的电脑上使用telnet程序，用它连接到[服务器](https://baike.baidu.com/item/服务器/100571)。[终端](https://baike.baidu.com/item/终端/1903878)使用者可以在telnet程序中输入命令，这些命令会在[服务器](https://baike.baidu.com/item/服务器/100571)上运行，就像直接在服务器的控制台上输入一样。可以在本地就能控制[服务器](https://baike.baidu.com/item/服务器/100571)。要开始一个telnet会话，必须输入用户名和密码来登录[服务器](https://baike.baidu.com/item/服务器/100571)。Telnet是常用的[远程控制](https://baike.baidu.com/item/远程控制/934368)Web[服务器](https://baike.baidu.com/item/服务器)的方法。

创建TCP服务器,通过telnet等工具连接TCP的服务端。

```js
const net =require('net')
const server=net.createServer(socket => {
    console.log('someone connects')
})
server.listen(8001,()=>{
    console.log('server is listening.')
})
```

### setInterval(cb, ms)

**setInterval(cb, ms)** 全局函数在指定的毫秒(ms)数后执行指定函数(cb)。

返回一个代表定时器的句柄值。可以使用 **clearInterval(t)** 函数来清除定时器。

setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。

### node多进程、restfuiapi

### express程序生成器，类似vue脚手架

npm install express-generator -g

express --no-view myapp

npm start

中间件可以理解为一个独立于主要功能逻辑的代码块，用于实现一些附加的功能，可以在主要逻辑处理之前或处理之后访问，类似于vue的导航守卫。

一些DNS服务器的ip地址有8.8.8.8、114.114.114.114

### 解决跨域的三种方法：

1、设计反向代理，解决跨域问题

2、使用JSONP，允许用户传递一个callback参数给服务器

3、在服务器端设置res的头部信息，允许所有请求或部分指定来源（确定的IP或者IP段）的请求

### 静态资源服务器：

apache、nginx、PHP自带的服务器等等

### 热更新工具：

supervisor、nodemon，用nodemon热启动比较方便

crypto加密

### 源：

nrm工具

![image-20230105195312060](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20230105195312060.png)
