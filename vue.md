# 什么是 MVVM

# 原理

数据劫持和观察订阅。

# Vue next-tick 的原理。

在事件循环中插入一个任务。

按照优先级使用

1. Promise；
2. MutationObserver；
3. setImmediate;
4. setTimeout

timerFunc 是一个函数，它的作用是在 Event Loop 中插入一个 Microtask 或 Macrotask。

如果是使用的是 Promise 或 MutationObserver，则将 isUsingMicroTask 这个 flag 置为 true。

# Diff 原理
