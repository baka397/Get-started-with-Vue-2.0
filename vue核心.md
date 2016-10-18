# vue核心

本章将重点说明vue中常用的核心方法，帮助学习者了解vue。在学习之前，我们先通过vue的生命周期图了解vue的整个流程，如下图。

![](http://vuejs.org/images/lifecycle.png)

1. 通过构造函数vue\(\)来创建实例，同时触发beforeCreate事件。
2. 初始化数据并执行init方法，此时触发created事件。
3. 在编译模板后，触发beforeMount，创建根节点[$el](http://vuejs.org/api/#vm-el)，触发mounted
4. 由于2.0引入了虚拟DOM，所以和react一样，现在在数据变更之后，会经过虚拟DOM的算法计算需要变更的内容，并最小化更新对应的DOM（此时会触发beforeUpdate和updated）。

5. 当$destory\(\)被执行时，会触发beforeDestroy，销毁相关监听、组件等内容并触发destroyed。

