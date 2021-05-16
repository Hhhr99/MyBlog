---
title: test
date: 2021-05-16
sidebar: auto
categories:
 - 摘记
---
# vue基础第一天

## `基础部分课程安排`

1. 第一天：Vue 模板语法
2. 第二天：Vue 进阶用法
3. 第三天：组件化开发
4. 第四天：路由机制



## 前言

​	本课程主要学习vue前端框架开发，遵循vue渐进式开发的设计思想，从模板视图渲染、模块组件化、路由、全局状态管理到大型应用的构建，根据这些模块本课程共分为三大模块，

- vue基础部分，主要学习模板视图渲染，组件，路由
- webpack构建工具部分，webpack和vue并没直接关系，只是目前市面较为流行的前端构建解决方案
- vue项目部分，开发一个主流的大型的商城管理后台应用，运用到上述提到的**渐进式**所有知识点

​	学习vue框架前需要具备的知识，要求熟练掌握html、css、JavaScript，已具备开发前端网页的能力，如果有其他框架的开发经验就更好了。

​	**记住，vue不是一门语言，只是通过JavaScript封装的一套前端框架，有自己独特的API和开发模式，所以我们现在所学习的只是按照vue作者设计的思路去开发，关键的底层还是在于JavaScript的基础知识，这往往是一个新手容易忽略的，切记！**

​	目前市面上的框架众多，vue只是其中一员，这里想要说明的是vue并不是唯一的解决方案，并且框架的内容也并不是一成不变的，随着版本的迭代和JavaScript语言标准的更新，框架内容可能会发生很大的变化， 正如上面所提到前端开发的重点还是在于JavaScript基础，所以在学习前必须再次强调，**不要对框架的任何内容进行死记硬背**，重点在于理解、练习和官网文档的查阅，比如某个功能自己不能单独实现，那么在找到解决思路后进行多次重复的练习，练习过程中遇到新的API要学会查阅文档，顺便还可以查看是否存在其他拓展功能。



## Vue 的介绍

### 多页应用和单页应用

### 传统多页应用

![01-传统单页应用](images\01-传统单页应用.png)

有一个带有三个页面的网站

- 网站首页
- 产品列表
- 用户中心

每个页面结构相同

- 顶部
- 底部
- 左边菜单
- 右边内容

**需求**

在每一个页面的左边菜单栏，添加（或者删除）广告

**实现方式**

- 修改首页
- 修改列表页
- 修改用户中心



### 单页应用

单页Web应用，就是：

如何以只有一个页面的方式显示多个页面的内容呢？

- 内容：一开始就会全部都在同一个页面上面
- 控制显示：js 控制内容显示

**使用单页应用实现增加广告的需求**

- 需求变动只需要修改一次

**小结**

单页应用就是先把所有的内容放在同一个页面上, 通过 js 控制显示切换, 目前的网页应用都是趋向于一种称为 **单页应用(SPA)** 的开发模式，这种模式我们不需要跳转到全新的页面，甚至不需要重新加载页面，只需要在一个模板上加载和卸载不同的子模板来显示不同的页面

![00-vue是开发单页应用的](images\00-vue是开发单页应用的.png)

**vue 开发的就是单页应用**



## Vue 简介

- 一套用于构建用户界面的渐进式框架。
- Vue 的核心库只关注视图层（模板渲染），易于上手。
- 结合多种工具和支持的库，Vue 也完全能够为复杂的单页应用提供驱动。

渐进式 JavaScript 框架

- 渐进式有一个特点，强制的编码要求较少。

- 按需要使用，不必一竿子把所有的东西都用上。
- 最核心的 vue，只是实现了模板引擎的自动渲染（声明式渲染）。

![02-vue是渐进式框架](images\02-vue是渐进式框架.png)



## 第一个vue案例-Helloworld

### 目标

了解vue.js的方式实现模板渲染

### 步骤

- 引入vue.js
- 添加一个模板结构
- 创建Vue实例
- 指定el和data的配置
- 在模板结构中添加插值表达式(输出表达式)

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <!-- 1.引入vue.js，只要引入了vue.js，就会在全局挂载一个Vue构函数 -->
  <script src="./js/vue.js"></script>
</head>

<body>
  <!-- 2.添加一个模块结构：控制vue所影响的范围 -->
  <div id="app">
    <!-- 5.添加模板dom结构 -->
    <h1>{{msg}}</h1>
    <h2>{{username}}</h2>
  </div>

  <script>
    // 3.创建一个vue实例,它可实现渲染（数据和模板的关联），所以你得告诉它你的模板和数据
    let VM = new Vue({
      // 4.添加配置
      // 4.1 el:指定模板，指定选择器，它就是后期vue实例所影响的范围
      el: '#app',
      // 4.2 data,data用于指定模板所对应的数据(业务处理数据)，它是一个对象
      data: {
        // msg: 'hello world',
        username: '60期的小伙伴'
      }

    })
  </script>
</body>

</html>
```



### 细节

- 引入vue.js之后，就会在全局挂载一个Vue构造函数
- 插值表达式只有写在模板结构中才会进行解析处理，写在外面会原样输出

### 错误信息

```tex
Property or method "***" is not defined on the instance but referenced during render
翻译：属性或方法***没有定义，但是在渲染的时候使用了
解决：确保在正确的位置正确的定义了***变量
```



## 什么是mvvm

- m：model:数据
- v:view:视图模板
- vm:vue实例，可以实现数据和模板的关联(渲染)
- 特点
    - 数据变化 ，模板视图自动刷新渲染
    - 模板视图中的数据变化 ，数据也会自动的变化





## 基于html版本的组件创建

### 概念

- html,css,js的结合，用于描述网页中的某个结构
- 以后可以复用的结构或者是业务逻辑比较复杂的结构都应该封装为组件
- 在vue中，组件的主要目的是功能拆分和代码维护和复用

### 创建组件

```vue
Vue.component(组件名称,{
	template:'组件的模板结构',
	// 在ES6中，在 对象中定义函数可以使用：
	// 函数名称：function(){}
	// 函数名称(){}
	data(){}
})
```

```vue
// Vue.component(组件名称，组件配置)
    Vue.component('mycom', {
      // template:用于定义组件的模板结构
      template: `<div>
                  <h2>组件的名称：{{myname}}</h2>
                  <p>这是我组件的结构</p>
                  <button>点我啊</button>
                 </div>`,
      data() {
        return {
          myname: '60期'
        }
      }
    })
```



### 使用组件

- 组件当成自定义标签来使用

### 常见错误

```tex
1.Unknown custom element: <first> - did you register the component correctly? For recursive components, make sure to provide the "name" option.
翻译：未知的用户元素first,你是否正确的注册(创建)了这个组件呢？如果是递归组件调用，那么确保组件有name属性
原因：你没有在vue实例进行处理之前创建好这个first组件
解决：将全局组件在vue实例的 前面 创建好

2.The "data" option should be a function that returns a per-instance value in component definitions.
翻译：组件中的data选项必须是一个函数，同时函数要为每个实例返回一个值
原因：组件是可复用的，为了让每个组件可以维护一个属于自己的数据，要求data必须是一个函数
解决：将data定义为一个函数

3.data functions should return an object
翻译：data函数必须返回一个对象
解决：返回一个对象

4.Component template should contain exactly one root element. If you are using v-if on multiple elements, use v-else-if to chain them instead.
翻译：组件的模板只能包含一个根元素，除非你使用if分支进行判断
解决：将多个元素包裹到一个根元素中，这种根元素一般可以做为div

5.Property or method "name" is not defined on the instance but referenced during render. Make sure that this property is reactive
翻译：属性或方法name没有定义，但是在渲染的时候引用 了
解决：确保这个属性或方法你在合适的位置定义了
```



## 基于单文件组件演示案例的结构

> 生成一个脚手架项目
>
> 删除其中一些不需要的文件和代码
>
> - 删除HelloWorld.vue
> - 删除App.vue中的代码
> - 注释掉main.js中关于App.vue的引入
> - 我的上课演示文件都添加在components目录中

### 添加一个用于演示的单文件组件

### main.js中引入并渲染

```js
import App from './components/day1/01-第一个vue案例.vue'

Vue.config.productionTip = false

new Vue({
  render: h => h(App)
}).$mount('#app')
```



## 插值表达式

```js
<div>
    <h1>这个文件主要说明插值表达式的使用</h1>
    <!-- 1.基本使用:直接渲染指定名称的变量,变量需要先定义好 -->
    <p>{{msg}}</p>
    <!-- 2.可以在插值中使用api -->
    <p>{{msg.toUpperCase()}}</p>
    <!-- 3.可以进行字符串的拼接 -->
    <p>{{'我想对你说:' + msg}}</p>
    <p>我想对你说:{{msg}}</p>
    <!-- 4.可以使用三元表达式 -->
    <p>{{age>=18?'成年':'未成年'}}</p>

    <!-- 不要在插值里面使用自增或自减 -->
    <!-- <p>{{age++}}</p> -->
    <!-- 不能写js关键字或结构 -->
    <!-- <p>{{if(age>=18)}}</p> -->
  </div>
```



### 常见错误

```tex
Property or method "name" is not defined on the instance but referenced during render. Make sure that this property is reactive
翻译：你在组件实例中没有定义好name这个变量，但是在渲染时使用了
解决：定义好

avoid using JavaScript keyword as property name: "if"
解释：在{{}}不能写语句，只能写表达式
```



## v-text

- 功能：完全更新标签之间的内容
- 使用语法：v-text="变量"
- 特点
    - 可以直接指定数据
    - 可以拼接字符串
    - 可以调用api
    - 可以使用三元表达式

```html
<div>
    <h1>这个文件主要说明v-text的使用</h1>
    <p>作用:设置标签的文本内容</p>
    <p>{{msg}}</p>
    <!-- 直接设置变量,变量要先定义好 -->
    <p v-text='msg'></p>
    <p v-text='msg.toUpperCase()'></p>
    <p v-text="'我想对你说:'+msg"></p>
    <p v-text="age>=18?'成年':'未成年'"></p>
    <p v-text="msg">这里已经有内容了</p>
  </div>
```



## v-html

- 功能：完全更新标签之间的内容
- 使用语法：v-text="变量"
- 特性：可以解析网页结构

```vue
<template>
  <div>
    <h1>这个文件主要说明v-html的使用</h1>
    <p>v-html的特点:它可以解析html结构</p>
    <p>{{msg}}</p>
    <p v-text="msg"></p>
    <!-- 直接使用v-html指定数据 -->
    <p v-html="msg"></p>
    <p v-html="msg.toUpperCase()"></p>
    <p v-html="'拼个字符串'+msg.toUpperCase()"></p>
    <p v-html="age>=18?'成年':'未成年'"></p>

    <p>{{str}}</p>
    <p v-text="str"></p>
    <p v-html="str"></p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'hello',
      age: 20,
      str: '后台返回的内容<hr>'
    }
  }
}
</script>
```



## v-for



### 使用方式



### 示例



### key的说明





## v-model



## v-on

### 语法



### 函数定义的位置



### 事件处理函数的参数



### 修饰符





## v-bind



## v-show



## v-if





## 案例：数据展示

### 单文件组件的静态结构的准备

### 数据动态渲染



### 数据的添加



### 数据的删除



