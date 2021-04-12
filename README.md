# Front-End-Interview
前端面试知识点

#### html，css

- DOCTYPE

> <!DOCTYPE> 声明必须是 HTML 文档的第一行，位于 `<html>` 标签之前,
  <!DOCTYPE>不是html标签，它是指示浏览器页面使用哪种HTML版本进行编写的指令，
  在html 4.01中，<!DOCTYPE>声明引用DTD，以为html 4.01是基于SGML，DTD规定了标记语言的规则，这样浏览器才能正确的呈现内容
  而html 5不基于SGML，所以不需要引用DTD，直接使用<!DOCTYPE>就行

- 语义化标签

> 

- 行内元素/块级元素/空元素
- 定位（static，relative，position，fixed）
- 垂直居中方法
- 如何实现一个自适应的正方形
- 如何用css实现一个三角形
- 三栏布局
- 清除浮动的方法
- CSS的BFC的概念?
- CSS盒子模型，有哪两种？
- CSS选择器有哪些，哪些属性可以继承
- CSS的选择器优先级?
- CSS有哪些伪类
- CSS3有哪些新特性
- 弹性盒子的布局模型，并解释如何使用？
- 移动端多屏幕适配的通用方案有哪些，REM是什么含义?
- 多端兼容性的解决方案?

#### javascript，ES6

- 变量的声明方式有哪些？如何声明变量，可以具有块级作用域？
- let，const，var的区别
- Javascript的基本类型有哪些，到ES6中新增了哪些类型
- this
- bind，apply，call的区别
- 浅复制与深复制
- 闭包的概念是什么，闭包有是用？
- 柯里化，纯函数的概念
- 原型链继承的原理，如何通过原型链实现继承？
- cookie，sessionStorage，localStorage的使用与区别，说一下他们的操作api
- ES6中的常用语法有哪些？
- 箭头函数与普通函数的区别
- 变量的结构赋值
- ES6中的Symbol，Map，Set
- Promise的实现
- 谈谈Promise和Async/await对比的理解
- setTimeout和Promise在异步实现上，有什么区别？
- promise、async await、Generator的区别
- 正则表达式实现字符串的Trim？
- ES6静态属性，静态方法
- 说说你对ES6 proxy的理解
- JS模块化（commonjs/amd/cmd/es6）

#### vue

- 谈谈你对vue的理解

> 1，`vue`是渐进式的`javascript`框架、核心库加插件、动态创建用户几面（异步获取后台数据，数据展示在界面）
> 2，采用的式`MVVM`模式：代码简洁体积小（20kb min+gzip），运行效率高，适合移动PC端开发；本身只不关注`UI`（和`React`相似），可以轻松引入`vue`插件和第三方库进行开发

- 说一下`MVVM`模式

> `Model-View-ViewModel`, `Model`表示数据模型层，`View`表示视图层，`ViewModel`是`View`和`Model`层的桥梁，数据绑定到`ViewModel`层并自动渲染到页面中，视图变化通知`ViewModel`层更新数据

- vue的数据双向绑定（响应式数据）的原理？

> `Object.defineProperty`重新定义`data`中所有的属性，`Object.defineProperty`可以使数据的获取与设置增加一个拦截功能，拦截属性的获取，进行依赖手机，拦截属性的更新操作，进行通知。
> 具体过程：1，首先`vue`使用`initData`初始化用户传入的参数，2，然后使用`new Observer`对数据进行观测，如果数据是一个对象就会调用`this.walk(value)`对对象进行处理，3，内部使用`defineReactive`循环对象属性定义响应式变化，4，核心就是使用`Object.defineProperty`重新定义数据
![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a5a919f243644a3a0fbeaa884d2f9cd~tplv-k3u1fbpfcp-watermark.image)

- vue的生命周期，每个周期都能做那些事情？
- vue组件之间的传值(父子组件，兄弟组件)
- v-if和v-for作用在同一个节点上的优先级是怎样的？
- Vue中的watch，computed的却别
- 你对vue.js的template编译的理解
- 虚拟DOM为什么快
- NextTick 原理分析
- SSR
- vuex的实现原理
- vue-router

#### react

- React的生命周期？
- React组件间的数据传递（父子组件，兄弟组件之间）
- React组件的更新过程
- React的无状态组件
- 高阶组件的实现原理？
- React的hooks的理解
- Virtual-DOM本质是什么，怎么去理解其再重绘流程上的作用
- React中的refs
- React的优缺点
- redux数据流的原理？
- setState是同步还是异步，几个参数是什么含义？

#### 浏览器

- 从输入url到呈现页面的过程
- 强缓存、协商缓存、cdn缓存
- 跨域如何实现？（JSONP/CORS）
- 跨域时如何处理cookie
- 垃圾回收机制
- 原生DOM与事件相关
- 事件机制有哪些？
- 前端路由方式
- 重绘（Rapaint）和回流（Reflow）
#### 前端工程化(webpack)

> webpack也基本上成了必考的内容，一般会问是否配置过webpack、做过哪些优化之类的。

- webpack打包工具的执行过程
- webpack 热加载执行原理
- webpack-dev-server和http服务器如nginx有什么区别?
- 如何提高webpack的构建速度
- 用过哪些loader和plugin
- loader的执行顺序为什么是后写的先执行
- webpack配置优化
- webpack打包优化（happypack、dll）
- plugin与loader的区别
- webpack执行的过程
- 如何编写一个loader、plugin
- tree-shaking作用，如何才能生效

#### 网络知识

- 说说你对http的理解
- https与http的区别(https为什么比http安全，详细解答)
- GET与POST的区别，何时使用POST？
- HTTP状态码
- 一次完整的HTTP事务是怎样的一个过程？
- TCP/IP的三次握手
- 你对http2.0知道多少呢？
- 正向代理与反向代理
- DNS
- 你们对安全方面做了哪些操作？
- 什么是xss，如何预防
- 什么是csrf，如何预防
- 为什么会造成csrf攻击

#### 性能优化方面

- 首屏加载如何优化
- 一个网页从请求到呈现花了很长时间，如何排查
