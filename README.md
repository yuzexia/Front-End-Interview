# Front-End-Interview
前端面试知识点

## html，css

- DOCTYPE

> <!DOCTYPE> 声明必须是 HTML 文档的第一行，位于 `<html>` 标签之前,
> <!DOCTYPE>不是html标签，它是指示浏览器页面使用哪种HTML版本进行编写的指令，
> 在html 4.01中，<!DOCTYPE>声明引用DTD，以为html 4.01是基于SGML，DTD规定了标记语言的规则，这样浏览器才能正确的呈现内容
> 而html 5不基于SGML，所以不需要引用DTD，直接使用<!DOCTYPE>就行

- 语义化标签

> 元素本身传达了关于标签所包含内容类型的一些信息
> 1，代码结构：在页面没有css的情况下，也能够呈现出很好的内容结构；2，有利于seo：爬虫依赖标签来确定关键词的权重，因此可以和搜索引擎建立良好的沟通，帮助爬虫抓取更多的有效信息；3，提升用户体验：例如title，alt可以用于解释名称或者解释图片信息，以及label标签的灵活运用；4，便于团队开发和维护：语义化使代码更具可读性，让其他开发人员更加理解html结构，减少差异化；5，方便其他设备解析：如屏幕阅读器，盲人阅读器，移动设备等，以有意义的方式来渲染网页
> html5常用的语义元素：header,nav,article,section,aside

![html5语义化标签](https://img-blog.csdn.net/20180626164405788?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4MTI4MTc5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

> 常用的语义化标签：header,h1,h2,h3,h4,h5,h6,nav,main,footer,article,section,p,ul,ol,li,blockquote,a,strong,em,q,abbr,small

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
- flex布局

## javascript，ES6

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

## vue

- 谈谈你对vue的理解

> 1，`vue`是渐进式的`javascript`框架、核心库加插件、动态创建用户几面（异步获取后台数据，数据展示在界面）
> 2，采用的式`MVVM`模式：代码简洁体积小（20kb min+gzip），运行效率高，适合移动PC端开发；本身只不关注`UI`（和`React`相似），可以轻松引入`vue`插件和第三方库进行开发

- 说一下`MVVM`模式

> `Model-View-ViewModel`, `Model`表示数据模型层，`View`表示视图层，`ViewModel`是`View`和`Model`层的桥梁，数据绑定到`ViewModel`层并自动渲染到页面中，视图变化通知`ViewModel`层更新数据

- vue的数据双向绑定（响应式数据）的原理？

> `Object.defineProperty`重新定义`data`中所有的属性，`Object.defineProperty`可以使数据的获取与设置增加一个拦截功能，拦截属性的获取，进行依赖手机，拦截属性的更新操作，进行通知。
> 具体过程：1，首先`vue`使用`initData`初始化用户传入的参数，2，然后使用`new Observer`对数据进行观测，如果数据是一个对象就会调用`this.walk(value)`对对象进行处理，3，内部使用`defineReactive`循环对象属性定义响应式变化，4，核心就是使用`Object.defineProperty`重新定义数据

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a5a919f243644a3a0fbeaa884d2f9cd~tplv-k3u1fbpfcp-watermark.image)

- vue的事件绑定原理

> - 原生DOM的绑定：`vue`在创建真实DOM时会调用`createElm`，默认会调用`invokeCreateHooks`。会遍历当前平台下相对的属性处理代码，其中就有`updateDOMListeners`方法，内部会传入`add()`方法
> - 组件绑定事件，原生事件，自定义事件：组件绑定事件时通过vue中自定义的`$on`方法实现的。（可以理解为：组件的`nativeOnOn`等价于普通元素的`on`组件的`on`会单独处理）

- v-model中的实现原理以及如何自动逸v-model

> `v-model`可以看成是`value+input`方法的语法糖（组件），原生的`v-model`，会根据标签的不同生成不同的事件与属性，来解析一个指令
> 自定义：自己写`model`属性，里面放上`prop`和`event`

- vue为什么采用异步渲染呢？

> `vue`是组件级更新，如果不采用异步更新，那么每次更新数据都会对当前组件进行重新渲染，所以为了性能，`vue`会在本轮数据更新后，再异步更新视图，核心思想是`nextTick`.
> `dep.notify()`通知watcher进行更新，`sub[i].update`依次调用watcher的`update`，`queueWatcher`将watcher去重放入队列，`nextTick(flushSchedulerQueue)`在下一tick中刷新watcher队列（异步）。
- 了解nextTick吗?

> 异步方法，异步渲染最后一步，与js事件循环联系紧密。主要使用了宏任务微任务(`setTimeout`、`promise`那些)，定义了一个异步方法，多次调用`nextTick`会将方法存入队列，通过异步方法清空当前队列。

- vue的生命周期，每个周期都能做那些事情？

> - beforeCreate：实例初始化之后，数据观测之前调用
> - created：实例创建完之后调用，实例完成：数据观测、属性和方法的运算、`watch/event`事件回调，无`$el`。
> - beforeMount：在挂在之前调用，相关`render`函数首次被调用
> - mounted：模板html被新创建的`vm.$el`替换，并挂在到实例上去之后调用该钩子函数
> - beforeUpdate：数据更新前调用，发生在虚拟DOM重新渲染和打补丁，在这之后调用该钩子函数
> - updated：由于数据更改导致的虚拟DOM重新渲染和打补丁，在这之后会调用该钩子
> - beforeDestroy：实例销毁前调用，实例仍然可用
> - destroyed：实例销毁之后调用，调用后，Vue实例指示的所有东西都会解绑，所有事件监听器和所有子实例都会被移除

- 每个生命周期内部都可以做什么？

> - created：实例已经船舰完成，因为它最早触发的，所以可以进行一些数据、资源的请求
> - mounted：实例已经挂载，可以进行一些DOM操作
> - beforeUpdate：可以在这个钩子中进一步的更改状态，不会触发重渲染
> - updated：可以执行依赖于DOM的操作，但是要避免更改状态，可能会导致更新无限循环
> - destoryed：可以执行一些优化操作，清空定时器，解除绑定事件

> ajax放在哪个生命周期：一般放在`mounted`中，保证逻辑统一性，因为生命周期是同步执行的，`ajax`是异步执行的，多数服务端渲染`ssr`统一放在`created`中，因为服务端渲染不支持`mounted`方法。
> 什么时候使用beforeDestroy：当前页面使用`$on`，需要解绑事件，清除定时器，解除绑定事件，`scrollmousemove`。

- 父子组件生命周期调用顺序

> - 渲染顺序：先父后子，完成顺序：先子后父
> - 更新顺序：父更新导致子更新，子更新完成后父
> - 销毁顺序：先父后子，完成顺序：先子后父

- vue组件之间的通信(父子组件，兄弟组件)

> - 父子之间通信：父组件提供数据通过属性`props`传递给子组件；子组件通过`$on`绑定父组件的事件，再通过`$emit`触发自己的事件（发布订阅）
> - 利用父子关系`$parent`、`$children`


> 获取父子组件实例的方法：
> - 父组件提供数据，子组件注入。`provide`、`inject`
> - `ref`获取组件实例，调用组件的属性、方法
> - 跨组件通信`Event Bus(Vue.prototype.bus=new Vue)`其实基于`$on`与`$emit`
> - vuex状态管理实现通信

- vuex的工作原理

> Vuex是一个专门为vue.js应用程序开发的*状态管理模式*
> Vuex状态自管理应用包含以下几个部分：
> - state：驱动应用的数据源
> - view：以声明方式将state映射到视图(view)
> - actions：响应再view上的用户输入导致的状态变化，下图单向数据流示意图
![](https://vuex.vuejs.org/flow.png)

> vuex多组件共享状态，因单向数据数据流简洁性很容易被破坏
> - 多个视图依赖同一状态
> - 来自不同视图的行为需要变更同一状态

![](https://vuex.vuejs.org/vuex.png)

- 如何从真实DOM到虚拟DOM

> 涉及到vue中的模板编译原理，主要过程：
> - 将模板转换成`ast(abstract syntax tree抽象语法树)`，`ast`用抽象语法来描述真实的js语法（将真实DOM转换为虚拟DOM）
> - 优化树
> - 将`ast`树生成代码

- 用`VNode`来描述一个DOM结构

> 虚拟DOM就是一个对象来描述一个真实的DOM元素，
> - 1，将`template`（真实的DOM）转换成`ast`（抽象语法树）
> - 2，`ast`通过`codegen`生成`render`函数
> - 3，`render`函数里的`_c`方法将它转换为虚拟DOM

- diff算法

> - 事件复杂度：个树的完全`diff`算法是一个事件复杂度`O(n*3)`，vue进行优化转化为`O(n)`.
> - 理解：
>   - 最小化更新：`key`很重要，这个可以是这个节点的唯一标识，告诉`diff`算法，在更改前后这个是同一节点。
>       - 扩展：`v-for`为什么要有`key`，没有`key`会暴力复用，
>   - 只有是同一个虚拟节点才会进行精细化比较，否则就是暴力删除旧的，插入新的
>   - 只进行同层比较，不会进行跨层比较

> - diff算法的优化策略：四种命中查找，四种指针
>   - 1，旧前与新前（先比开头，后插入和删除节点的这种情况）
>   - 2，旧后与新后（比结尾，前插入和删除的情况）
>   - 3，旧前与新后（头与尾比，此种发生了，涉及移动节点，那么新前指向的节点，移动到旧后之后）
>   - 4，旧后与新前（尾与头比，此种发生了，涉及移动节点，那么新前指向的节点，移动到旧前之前）

- computed、watch和method

> - computed：默认`computed`也是一个具备缓存的`watcher`，只有当依赖的数据变化时才会计算，当数据没有变化是时，它会读取缓存数据，如果一个数据依赖于其他数据，使用`computed`
> - watch：每次都需要执行函数，`watch`更适用于数据变化的异步操作，如果需要在某个数据变化时做一些事情，用`watch`
> - method：只要把方法用在模板上了，每次变化都会重新渲染视图，性能开销大    

- `v-if`于`v-show`的区别

> - v-if: 如果条件不成立不会渲染当前指令所在的DOM元素
> - v-show：指示切换当前元素的显示于隐藏

- v-if和v-for作用在同一个节点上的优先级是怎样的？

> `v-for`比`v-if`的优先级更高，连用的话，会将`v-if`的每个元素都添加一下，造成性能问题

- `v-hmtl`会造成哪些问题

> - `xss`攻击
> - `v-html`会替换标签内部的元素

- 描述组件的渲染和更新的过程

> - 渲染组件，会通过`vue.extend()`方法构建子组件的构造函数，并进行实例化，最终手动调用`$mount()`进行挂载
> - 更新组件：更新组件时会进行`patchVnode`流程，核心是`diff`算法

- vue组件中的data为什么时函数

> 主要目的是：避免组件之间的数据互相影响，同一个组件被复用多次会创建多个实例，如果`data`是一个对象的话，这些实例用的是同一个构造函数。为了保证组件的数据独立，要求每个组件都必须通过`data`函数返回一个对象作为组件的状态。

- action于mutation的区别

> - mutation：是同步操作，`$watch`严格模式下会报错
> - action：是异步操作，可以获取数据之后，调用mutation提交最终数据

- `keep-alive`的理解

> `keep-alive`可以实现组件的缓存，当组件切换时不会会当前组件进行卸载，常用的2个属性`include`、`exclude`，2个生命周期`activated`、`deactivated`

- 为什么要使用异步组件

> - 1，节省打包出的结果，异步组件分开打包，采用`jsonp`的方式进行加载，有效解决文件过大的问题
> - 2，核心就是把组件变成一个函数，依赖`import()`语法，可以实现文件的分割加载。

- vue性能优化

> 1，编码优化
>   - 事件代理
>   - `keep-alive`
>   - 拆分组件
>   - `key`保证唯一性
>   - 路由懒加载、异步组件
>   - 防抖节流
> 2，vue加载性能优化
>   - 第三方模块按需引入(`babel-plugin-component`)
>   - 图片懒加载
> 3，用户体验
>   - `app-skeleton`骨架屏
>   - `shellapp` 壳
>   - `pwa`
> 4，seo
>   - 预渲染

- 你对vue.js的template编译的理解
- 虚拟DOM为什么快
- NextTick 原理分析
- SSR
- vue-router

> `vue-router`是vue.js官方的路由管理器，它和vue.js核心深度集成，让构建单页应用更简单
> 主要组件：`<router-link>`、`<router-view>`、`<keep-alive>`

- `active-class`是哪个组件的属性？

> `active-class`是`<router-link>`的属性，用来做选中样式的切换，当`router-link`标签被点击时，将会应用这个样式

- vue-router的动态路由

> - 动态路由的创建主要使用`path`属性，使用动态路径参数，以冒号开头

```js
{
    path: 'details/:id',
    name: 'Details',
    compontents: Details
}
```
> 访问details目录下的所有文件，如`details/a`,`details/b`，都会映射到Details组件上

> - 当匹配到/details下的路由时，参数值会被设置到`this.$route.params`下，所以通过该属性可以获取动态参数

```js
console.log(this.$route.params);
```

- `vue-router`有几种导航钩子

> - 全局前置守卫
>   ```js
>       const router = new VueRouter({});
>       router.beofreEach((to, from, next) => {
>           // to do somethings
>       })
>   ```
>   - to: Route 代表要进入的目标路由，它是一个路由对象
>   - from：Route 代表当前正要离开的路由，它是一个对象
>   - next: Function 必须需要调用的方法，具体的执行效果则依赖next方法调用的参数
>       - next():进入管道中的下一个钩子，如果全部的钩子执行完了，则导航的状态就是comfirmed(确认的)
>       - next(false):终端当前的导航，如果浏览器URL改变，那么URL会重置到from路由对应的地址
>       - next('/') || next({path: '/'}):跳转到一个不同的地址，当前当行终端，执行新的导航
>   - *next方法必须调用，否则钩子函数如法resolved
> - 全局后置钩子
>   ```js
>       router.afterEach((to, from) => {
>           // to do somethins
>       })
>   ```
>   - 后置钩子并没有next函数，也不会改变导航本身
> - 路由独享钩子
>   - beforeEnter
>       ```js
>           const router = new VueRouter({
>               routes: [{
>                   path: '/home',
>                   component: Home,
>                   beforeEnter: (to, from, next) => {
>                       // to do somethins
>                       // 参数于全局守卫参数一样
>                   }
>               }]
>           })
>       ```
> - 组件内导航钩子

- `$route`和`$router`的区别是什么？

> - `$router`是`VurRouter`的实例，是一个全局路由对象，包含了路由跳转的方法、钩子函数等
> - `$route`是路由信息对象/跳转的路由对象，每一个路由都会有一个`router`对象，是一个局部对象，包含`ptah, params, hash, query, fullPath, matched, name`等路由信息参数

- vue-router响应路由参数的变化

> - 用watch检测
> ```js
>   watch: {
>       $route(to, from) {
>           console.log(to.path);   
>           // 对路由变化做出响应
>       }
>   }
> ```
> - 组件内导航钩子函数
> ```js
>   beforeRouteUpdate(to, from, next) {
>       // to do somethings
>   }
> ```

- vue-router传参方式

> - Params
> - Query

- vue-router的两种模式

> - hash
>   - 原理是onhashchange事件，可以在window对象上监听这个事件
>   ```js
>       window.onhashchange = function(event) {
>           console.log(event.oldURL, event.newURL);
>           let hash = location.hash.slice(1)
>       }
>   ```
> - history
>   - 利用html5 history interface中新增的`pushState()`和`replaceState()`方法
>   - 需要后台配置支持，如果刷新时，服务器没有响应资源，会显示404

- vue-router懒加载的实现方式

> - 当打包构建应用时，Javascript包会非常大，影响页面加载。如果我们**能把不同路由对应的组件分割成不同代码块，然后当路由被访问时再加载对应组件**，这样就更高效了。
> - 结合vue的[异步组件](https://cn.vuejs.org/v2/guide/components-dynamic-async.html#%E5%BC%82%E6%AD%A5%E7%BB%84%E4%BB%B6)和webpack的[代码分割功能](https://doc.webpack-china.org/guides/code-splitting-async/#require-ensure-/)，可以实现实现路由组件的懒加载
> - 配置懒加载的步骤
>   - 1，将异步组件定义为返回一个Promise的工厂函数（该函数返回的Promise应该时resolve组件本身）
>   ```js
>       const Foo = () => {
>           Promise.resolve({
>               /*组件定义对象*/
>           })
>       }
>   ```
>   - 2，在webpack中，使用动态import语法来定义代码分快点（split point）
>   ```js
>       import('./Foo.vue'); // 返回Promise
>   ```
>   - 3， 结合这两者，这就是如何定义一个能够被 Webpack 自动代码分割的异步组件。
>   ```js
>       const Foo = () => import('./Foo.vue);
>   ```
>   - 4，在路由配置中什么都不需要改变，只需要像往常一样使用 Foo：
>   ```js
>       const router = new VueRouter({
>           routes: [{path: './foo, component: Foo}]
>       })
>   ```
> - 把组件按组分块
>   - 有时候我们想把某个路由下的所有组件都打包在同个异步块 (chunk) 中。只需要使用 命名 chunk，一个特殊的注释语法来提供 chunk name (需要 Webpack > 2.4)
>   ```js
>       const Foo = () => {/*webpackChunkName: "group-foo"*/ './Foo.vue'}
>       const Bar = () => {/*webpackChunkName: "group-bar"*/ './Bar.vue'}
>       const Baz = () => {/*webpackChunkName: "group-baz"*/ './Baz.vue'}
>       /*Webpack 会将任何一个异步模块与相同的块名称组合到相同的异步块中*/
>   ```
## react

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

## 浏览器

- 从输入url到呈现页面的过程
- 强缓存、协商缓存、cdn缓存
- 跨域如何实现？（JSONP/CORS）
- 跨域时如何处理cookie
- 垃圾回收机制
- 原生DOM与事件相关
- 事件机制有哪些？
- 前端路由方式
- 重绘（Rapaint）和回流（Reflow）
## 前端工程化(webpack)

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

## 网络知识

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

## 性能优化方面

- 首屏加载如何优化
- 一个网页从请求到呈现花了很长时间，如何排查
