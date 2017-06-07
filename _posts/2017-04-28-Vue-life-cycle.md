---
layout: post
title:  "Vue life cycle "
date:   2017-04-28 15:57:35 +0800
categories: Vue
---

#### vue 生命周期
![](https://cn.vuejs.org/images/lifecycle.png)

# vue生命周期 #
Vue实例有一个完整的生命周期，从开始创建、初始化数据、编译模板、挂载Dom、渲染→更新→渲染、卸载等一系列过程，我们称这是Vue的生命周期。通俗说就是Vue实例从创建到销毁的过程，就是生命周期。


## beforeCreate ##
- 在实例初始化之后，数据观测(data observer) 和 event/watcher 事件配置之前被调用。

## created ##
-  在实例创建之后同步调用。此时实例已经结束解析选项，这意味着已建立：数据绑定，计算属性，方法，watcher/event 回调。
-  但是还没有开始 DOM 编译，$el 还不存在,但是实例存在,即this.a存在,可打印出来 。

## beforeCompile ##
- 未开始编译

## compiled ##
- 在编译结束后调用。此时所有的指令已生效，因而数据的变化将触发 DOM 更新。但是不担保 $el 已插入文档

## beforeMount ##
- 在挂载开始之前被调用：相关的 render 函数首次被调用。

## mounted ##
- el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。如果 root 实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内。

## beforeUpdate ##
- 数据更新时调用，发生在虚拟 DOM 重新渲染和打补丁之前。 你可以在这个钩子中进一步地更改状态，这不会触发附加的重渲染过程。

  **该钩子在服务器端渲染期间不被调用。**

  ​

## updated ##
- 由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。

- 当这个钩子被调用时，组件 DOM 已经更新，所以你现在可以执行依赖于 DOM 的操作。然而在大多数情况下，你应该避免在此期间更改状态，因为这可能会导致更新无限循环。

  **该钩子在服务器端渲染期间不被调用。**

  ​


## activated ##
- keep-alive 组件激活时调用。

  **该钩子在服务器端渲染期间不被调用。**

  ​

## deactivated ##
- keep-alive 组件停用时调用。

  **该钩子在服务器端渲染期间不被调用。**

  ​

## beforeDestroy ##
- 触发方式,在console里面打myVue.$destroy();

- 实例销毁之前调用。在这一步，实例仍然完全可用。

  **该钩子在服务器端渲染期间不被调用。**

  ​

## destroyed ##
- 触发方式,在console里面打myVue.$destroy();其中myVue.$destroy(true)是删除DOM节点,会触发detached函数,但是实例仍然存在.

- Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。

  **该钩子在服务器端渲染期间不被调用。**

  ​