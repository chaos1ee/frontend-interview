# Event Loop

# 请实现一个 cacheRequest 方法，保证发出多次同一个 ajax 请求时都能拿到数据，而实际上只发出一次请求

```javascript
const request = (url, options) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve({ url, data: options, state: "Success" });
    }, 2000);
  });
};

const PENDING = 0;
const SUCCESS = 1;
const FAILED = 2;

const cache = new Map();

const cacheRequest = (url, options) => {
  let key = `${url}:${option.method}}`;

  if (cache.has(key)) {
    if (cache.get(key).status === PENDING) {
      return cache.get(key).promise;
    }

    return Promise.resolve(cache.get(key).data);
  } else {
    const requestApi = request(url, options);

    cache.set(key, { status: PENDING, promise: requestApi });

    return requestApi
      .then((res) => {
        cache.set(key, { status: SUCCESS, data: res });
        return Promise.resolve(res);
      })
      .catch((err) => {
        cache.set(key, { status: FAILED, data: err });
        Promise.reject(err);
      });
  }
};
```

# 实现观察订阅

```javascript
class Event {
  constructor() {}

  on() {}

  off() {}

  emit() {}

  once(event, listener) {
    const func = () => {
      const args = [].slice.call(arguments);
      listener.apply(null, args);
      this.off(event, func);
    };

    this.on(event, func);
  }
}
```

# bind 函数实现

```javascript
// 需要注意this指向
Function.prototype.bind = function bind(context, ...args1) {
  return (...args2) => this.apply(context, [...args1, ...args2]);
};
```

# 手写 reduce

```js
Array.prototype.reduce = function () {
  const cb = arguments[0];
  const initialVal = arguments[1] ? arguments[1] : undefined;

  let ret;

  for (let i = 0; i < this.length; i++) {
    if (!initialVal) {
      initialVal = cb(this[i], this[i + 1], i, this);
      i++;
    } else {
      ret = cb(initialVal, this[i], i, this);
    }
  }

  return ret;
};
```

# 节流防抖

```javascript
function debounce(func, wait, immediate) {
  let timer;
  return function () {
    const context = this;
    const args = arguments;

    if (timer) clearTimeout(timeout);

    if (immediate) {
      timer = setTimeout(function () {
        timer = null;
      }, wait);
      func.apply(context, args);
    } else {
      timer = setTimeout(function () {
        func.apply(context, args);
      }, wait);
    }
  };
}
```

# 变量未定义与未赋值的区别

变量未定义，会报错：

> Uncaught ReferenceError: xxx is not defined

变量已声明未赋值，该变量的初始值即为 undefined，类型为 undefined。

# 使用 Promise 模拟超时

将 setTimeout 和请求分别包装成 Promise 类型的数据，然后放置到 Promise.race 中。

```javascript
const request = new fetch(url, {
  method: "post",
});

const timer = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject("Timeout");
  }, 5000);
});

Promise.race([request, timer])
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.err(err);
  });
```

# import 与 require 的区别

1. 属于不同的标准。import 属于 ECMAScript2015 规范，require 属于 commonjs 规范。
2. 加载时间点不一样。require 是动态加载，import 是静态加载（也就是编译的时候就加载了）。
3. 输出值不一样。require/exports 的输出是值的拷贝，import/export 的输出值是引用。

# 隐式转化

# 跨域

# 继承
