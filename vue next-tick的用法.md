## vue next-tick的用法





## 计算timerFunc。

按照优先级使用

1. Promise；
2. MutationObserver；
3. setImmediate;
4. setTimeout

timerFunc是一个函数，它的作用是在Event Loop中插入一个Microtask或Macrotask。

如果是使用的是Promise或MutationObserver，则将isUsingMicroTask这个flag置为true。

## nextTick函数

