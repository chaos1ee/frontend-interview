# Webpack Plugin

## plugin的组成部分

主要由以下部分组成：

- 必须是命名函数或类；
- 在对象的原型上定义 `apply` 方法；
- 指定要的插入的事件钩子；
- 处理webpackne内部实例的特定数据；
- 功能完成后调用webpack提供的回调函数。



例如：

```javascript
class MyExampleWebpackPlugin {
  apply(compiler) {
    compiler.hooks.emit.tapAsync('MyExampleWebpackPlugin', (compilation, callback) => {
      console.log('This is an example plugin!');
      
      compilation.addModule(/* ... */);
      
      callback();
    })
  }
}
```

