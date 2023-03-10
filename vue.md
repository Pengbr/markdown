MVVM框架

view层：视图层，在前端开发中，通常就是dom层，主要的作用是给用户展示各种信息

model层：数据层，数据可能是我们固定的死数据，更多的是来自我们的服务器，从网络上请求下来的数据

vuemodel层：视图模型层，是view和model沟通的桥梁，一方面它实现了data binding，也就是数据绑定，将model的改变事实反应到view中，另一方面它实现了dom listener，也就是dom监听，当dom发生一些事件（点击、滚动、touch等）时，可以监听到，并在需要的情况下改变对应的data



v-bind  可简写为冒号： **动态绑定**属性

v-on  可简写为@  绑定事件监听

v-model 双向监听

组件化：分而治之的思想

Vue 实例还暴露了一些有用的实例 property 与方法。它们都有前缀 `$`，以便与用户定义的 property 区分开来。

template标签不影响结构

diff算法对比虚拟dom，通过key进行对比，key是虚拟dom的标识

set与get方法实现响应式（v-model的底层原理）Vue.set()添加属性

数据劫持

vue监视数据的原理

xss攻击，盗走cookies。通过cookie-editor插件可以快速的导入和导出cookie

**节流与防抖**

vue自定义指令：directives

自定义指令的钩子函数：bind、inserted、update；自定义指令命名方式：kebab-case，kebab烤肉串

js debugger语句

组件就是一块砖，哪里需要哪里搬

组件的本质是一个名为VueComponent的构造函数，组件中的this指向VueComponent实例对象



## [实例生命周期钩子](https://cn.vuejs.org/v2/guide/instance.html#实例生命周期钩子)

每个 Vue 实例在被创建时都要经过一系列的初始化过程——例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会。

vue实例中可以创建生命周期函数

![Vue 实例生命周期](https://cn.vuejs.org/images/lifecycle.png

spa(simple page web application) 单页面应用  通过前端路由跳转页面



![image-20210714204624263](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210714204624263.png)

v-for与key连用



## 配置文件分离

区分开发环境与生产环境

开发环境（development）：开发环境是程序猿们专门用于开发的服务器，配置可以比较随意， 为了开发调试方便，一般打开全部错误报告。(程序员接到需求后，开始写代码，开发，运行程序，看看程序有没有达到预期的功能；)

测试环境（testing）：一般是克隆一份生产环境的配置，一个程序在测试环境工作不正常，那么肯定不能把它发布到生产机上。(程序员开发完成后，交给测试部门全面的测试，看看所实现的功能有没有bug，测试人员会模拟各种操作情况；)

生产环境（production）：是指正式提供对外服务的，一般会关掉错误报告，打开错误日志。(就是线上环境，发布到对外环境上，正式提供给客户使用的环境。)

三个环境也可以说是系统开发的三个阶段：开发->测试->上线，其中生产环境也就是通常说的真实环境。



## vue cli与vue router

脚手架：建筑工程名词。

render渲染

template--->ast--->**render--->virtual dom--->ui**

vue创建脚手架  vue create 项目名称

终端中输入 vue ui 进入图形化配置界面

前端路由与后端路由   vue-router    router-link   router-view       spa单页面富应用，一个组件就是一个页面

router-link类似于a标签，router-link可以跳转路由

路由懒加载，将路由一个一个的组件打包到不同的JS文件中，需要是再从服务器请求

路由的嵌套，子路由（二级路由）

入口文件（main.js)、根组件(app.vue)、子组件（路由）(xxx.vue)

**url的完整组成：协议：//host:端口(80)/path?查询(query)#fragment**

动态路由里面可以接收参数，API是params

$router与$route，$router是所有的路由，$route是当前活跃的路由

导航守卫    meta元数据     钩子函数（hook)（回调）

前置守卫（guard)，后置钩子（hook）

vue的生命周期，组件也具有生命周期

keep-alive保证组件不被销毁

svg格式：可缩放矢量图形

![image-20210807155927503](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210807155927503.png)

项目基本结构

组件化开发：组件树



## vuex

状态管理模式

$store

mutations突变，改变state通过mutation，不要再mutation中进行异步操作

state单一状态树，单一数据源。vue框架有很多树的思想。

响应式：数据发生变化时界面也会发生更新，vue新版本的响应式更好

action类似mutation，用来放异步操作

![image-20210818093254045](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210818093254045.png)



## axios

nginx代理服务器

axios拦截器     比如config中一些信息不符合服务器的要求，比如每次发送网络请求时，都希望在界面中显示一个请求的图标，某些网络请求（比如登录token）必须携带一些信息。（请求拦截的作用）

interceptor拦截器

token就是代替session-cookie机制的存储用户状态的令牌。



## 项目

git clone https://github.com/Pengbr/supermall.git

git add .

 git commit -m '初始化项目'

 git push

划分项目结构

在CSS中@import是导入CSS样式表，这种方式通常会在CSS文件中使用，这样做的好处是，可以把多个样式表导入到一个样式表中，从而在页面里面只需要导入一个样式表即可。

文件夹一般小写，组件一般大写

架构思想：分层思想，降低耦合。高内聚，低耦合。

js中的GC机制，当变量没用被引用时会回收

v-bind当需要动态绑定属性时使用,父传子用props

flex:1表示均等分

做项目实现功能的同时也要保证代码的优雅以方便后期的维护

请求后端数据--->数据展示



npm run serve启动服务；npm run build打包



## 其它

vue框架定义了一个非常有用的vue实例property属性的概念。需要注意的是，在使用该功能时必须要加上前缀$符号，主要是便于与用户定义的数据property属性进行区分。

vue内部定义了一个观察函数$watch()、事件触发方法$emit()、自定义事件方法$on、$once

vm中所具有的属性都可以在模板中直接使用

**代理模式**

meta键  即win键

深度监视 deep:true 

生命周期钩子函数

<template>标签是vue框架自带的，本质上是一个虚拟元素，在最终的页面代码中是不体现的，其更像是一个一个抽象的页面元素包裹器。
vue中的指令修饰符：.prevent阻止默认行为，.stop阻止冒泡，.once强制执行仅仅一次有效的事件行为。
v-model指令的修饰符：.trim强制去除空格，.lazy，.number
$emit对象的作用是子组件向父组件暴露方法

路由嵌套与子路由（children）

vue-router提供了针对路由的导航守卫，可以在路由变化时执行一些代码，类似于某些开发框架中的中间件概念，可以针对全局路由或某一个特定路由。$router与$route

vuex状态管理工具(数据需要共享时使用)，只适用于大中型的单页面应用，小型页面不需要。$store

vue ui     element ui 、ant design、view ui等等

计算属性落脚点在属性，而方法落脚点在方法

**路径参数与查询参数：**

1.一个“路径参数”使用冒号 : 标记。当匹配到一个路由时，参数值会被设置到 this.$route.params，可以在每个组件内使用。

我们经常需要把某种模式匹配到的所有路由，全都映射到同个组件。例如，我们有一个 User 组件，对于所有 ID 各不相同的用户，都要使用这个组件来渲染。以下代码的效果就会把 /user/foo 和 /user/bar 都将映射到相同的路由。

```vue
const User = {
  template: '<div>User</div>'
}

const router = new VueRouter({
  routes: [
    // 动态路径参数 以冒号开头
    { path: '/user/:id', component: User }
  ]
})
```

也可以在一个路由中设置多段“路径参数”，对应的值都会设置到 `$route.params`

![img](https://img-blog.csdnimg.cn/20200527113340803.png)

2.查询参数，一个“查询参数”使用问号 ? 标记
一个 key/value 对象，表示 URL 查询参数。例如，对于路径 /foo?user=1，则有 $route.query.user == 1，如果没有查询参数，则是个空对象。

### 过滤器

Vue.js 允许你自定义过滤器，被用作一些常见的文本格式化。由"管道符"指示, 格式如下：

```vue
<!-- 在两个大括号中 -->
{{ message | capitalize }}

<!-- 在 v-bind 指令中 -->
<div v-bind:id="rawId | formatId"></div>
```

**过滤器函数**接受表达式的值作为第一个参数。以下实例对输入的字符串第一个字母转为大写：

```vue
<div id="app">
  {{ message | capitalize }}
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: 'runoob'
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
</script>
```

v-model指令可以由v-on和v-bind替代。

在一个组件中使用另外一个组件就能构成父子组件关系。

区分全局组件与局部组件、父组件与子组件。

data写成函数形式有自己的作用域，可以避免组件之间产生不必要的相互影响。

全局组件不需要注册可以直接使用，局部组件需要注册到vue实例下。通过props进行父子组件间的通信。

### 为什么需要JSONP?

由于浏览器安全限制,数据是不可以直接跨域(包括不同的根域名、二级域名、或不同的端口)请求的,除非目标域名授权你可以访问。



## [vue实例和vue组件有什么不同](https://chaihongjun.me/javascript/280.html)

app.vue是根组件

经过Vue组件的学习，发现Vue组件和我们new Vue实例化的对象有些相似以及不同的地方。

首先相同的地方：

1. 通过new实例化Vue实例对象的时候传入的参数是一个对象，这个对象里面有很多的Vue选项可以使用，比如el,data,computed,methods,components等等
2. 同样的通过Vue.component方式声明的全局组件，它的第二个参数也是一个对象，同样也是里面包含很多可用的选项,data,computed,methods,components等等

不同的地方，组件的data是一个function，组件没有el挂载点这个选项。除了这两点，实际基本上可以将Vue实例与Vue组件等同于一个东西来看待。

**可以想象我们平时new Vue的实例对象当作一个根组件**，这个根组件内部可以含有子组件，这个根组件位于整个组件树的最上层。然后，我们自己创建的组件，一般可以视为子组件，这些组件可以放到根组件内。另外，还有一些所谓的游离组件，通过new Vue().$mount()的方式挂载到页面上，比如页面右侧的客服悬浮窗，比如一些弹窗等等，不属于整个页面整体主要部分，当然这些游离的组件也可以有它们自己的子组件。

对于SPA单页面应用，URL不发生实际跳转，一般通过路由构建SPA结构，SPA的根组件就变成这个应用的组件树的始祖，所以也就是一般意义上SPA只有一个根组件。

所以，可以理解成整个页面是由多个层级的组件构成的，亦或是多个Vue实例组合而成。
