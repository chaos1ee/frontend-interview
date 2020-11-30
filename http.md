# HTTP 缓存

## 缓存的分类

- 强缓存。服务器通知浏览器一个时间，下次请求的时候，若在有效期内直接使用缓存。若已经过期，则执行比较缓存策略。
- 协商缓存。客户端与服务器之间协商是否命中缓存。

HTTP 请求都是从第二次请求开始的：

- 第一次请求资源时，服务器返回资源，并在 response header 中回传资源的缓存策略；
- 第二次请求时，浏览器判断请求是否命中缓存，命中强缓存就直接返回 200，否则就将请求参数添加到 request header 中，看是否命中协商缓存，命中则返回 304，否则就返回新的资源。

## 强缓存

cache-control 与 expires

Cache-Control 中的 max-age 属性 是一个相对时间，用以表示自上次返回资源后多少秒的时间内缓存有效。Expires 是一个绝对时间，表示在有效期内直接读取缓存，不发送 HTTP 请求。Cach-Control 的优先级比 Expiress 高。

### Cache-Control

包含的属性：

- no-store：不缓存，每次都重新请求。
- no-cache： 每次都要向服务器验证缓存是否过期。
- private： 只有客户端可以缓存，代理服务器不能缓存。
- public：客户端与代理服务器都可以缓存。
- max-age：至上一次成功请求资源多少秒后资源过期。
- must-revalidate：如果超过了 `max-age` 的时间，浏览器必须向服务器发送请求，验证资源是否还有效。

### expires

## 协商缓存

有两对头部都可以实现协商缓存：last-modified/if-modified-since 和 e-tag/if-none-math。

        first time request

client --------------------> server

        last-modified: xxx

client <-------------------- server

        if-modified-since: xxx

client --------------------> server

e-tag/if-none-math 与 last-modified/if-modified-since 的原理类似的，只不过 e-tag 是依靠算法计算文件内容得到的。

# TCP 为什么是可靠的

https://blog.csdn.net/Awille/article/details/79748193

# TCP 为什么要三次握手四次挥手
