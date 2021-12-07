---
title: vue3新特性对比vue2.x
date: 2021-12-07 13:57:29
tags:
---

# 一、根标签

> Vue2 的`Templata`只支持一个根标签  
> Vue3 的`Templata`支持多个根标签

    //vue2
    <template>
      <div></div>
    </template>

    // vue3
    <template>
      <div></div>
      <img/>
    </template>

# 二、初始化方法

> Vue2 使用 `new Vue()`, 参数是`new Vue({template, render})`  
> Vue3 使用 `createApp()` 参数是 `createApp(组件)`

    //vue2
    import Vue from 'vue';
    import router from './routers/';
    import store from './stores';
    import App from './App.vue';
    const app =  new Vue({
      router,
      store,
      render: h => h(App)
    }).$mount('#app');

    // vue3
    import { createApp } from 'vue';
    import App from './App.vue';
    import { router } from './router';
    const app = createApp(App).use(router).mount('#app');

# 三、vue3 内置组件 teleport

> 将 teleport 包裹的元素移动到某个 DOM 节点下  
> 有两个参数 to - string；disabled - boolean

to 使用方法：

    <!-- 正确 -->
    <teleport to="body" />
    <teleport to="#some-id" />
    <teleport to=".some-class" />
    <teleport to="[data-teleport]" />

    <!-- 错误 -->
    <teleport to="h1" />
    <teleport to="some-string" />

disabled 使用方法：

> 此可选属性可用于禁用 <teleport> 的功能，这意味着其插槽内容将不会移动到任何位置，而是在您在周围父组件中指定了 <teleport> 的位置渲染。

    <teleport to="#popup" :disabled="displayVideoInline">
      <video src="./my-movie.mp4" />
    </teleport>

# 四、Lifecycle Hooks

> 新版的生命周期函数，可以按需导入到组件中，且只能在 setup() 函数中使用.

- beforeCreate -> use setup()
- created -> use setup()
- beforeMount -> onBeforeMount
- mounted -> onMounted
- beforeUpdate -> onBeforeUpdate
- updated -> onUpdated
- beforeDestroy -> onBeforeUnmount
- destroyed -> onUnmounted
- errorCaptured -> onErrorCaptured
