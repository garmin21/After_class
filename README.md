### 会话

```json
由于 HTTP 协议是无状态的协议，所以服务端需要记录用户的状态时，就需要用某种机制来识别具体的用户，这个机制就是会话（Session）。
cookie 与 session 的区别?
    cookie 存储在浏览器（有大小限制），session 存储在服务端（没有大小限制）
    通常 session 的实现是基于 cookie 的，session id 存储于 cookie 中
    session 更安全，cookie 可以直接在浏览器查看甚至编辑
```

```json
我们通过引入 express-session 中间件实现对会话的支持：
app.use(session(options))
```

```json
session 中间件会在 req 上添加 session 对象，即 req.session 初始值为 {}，当我们登录后设置 req.session.user = 用户信息，返回浏览器的头信息中会带上 set-cookie 将 session id 写到浏览器 cookie 中，那么该用户下次请求时，通过带上来的 cookie 中的 session id 我们就可以查找到该用户，并将用户信息保存到 req.session.user。
```

