有状态  无状态



为了解决这个问题出现了session与cookie技术



cookie(是一个对象)：

实际上一小段文本信息（4kb），客户端请求服务器之后，如果需要记录用户状态，就是用response向客户端浏览器颁发cookie。而客户端的浏览器会把cookiec储存起来



*cookies里只能放string*

stringify：字符串化

parse：解析



cookies  { maxAge: 4 * 1000 }过期时间(4s)

{ maxAge: 24 * 60 * 60 * 1000 }(一天  加8)

HttpOnly :值为true时，cookie只能通过服务器端修改，不能通过js修改



session(是一种机制）：执行session这个机制时，会生成session的id，通过id去服务端获取相应的数据

```js
npm i koa-session --save

const session = require('koa-session')

app.keys = ['liu']
const CONFIG = {
    key: 'koa.sess'

}
.use(session(CONFIG, app))

```







```js
npm i koa2-cors --save

const cors = require('koa2-cors');

.use(cors({
    credentials: true,
  }))


```







#### session与cookies关系，异同：

1.cookie的客户端限制是4k，就是说一个站点在客户端存放的cookie不能超过4k；

2.cookie不是很安全，别人可以分析存在本地的cookie并进行cookie欺骗，考虑到安全应当使用session；

3.cookie数据放在客户的浏览器（客户端）上，session数据放在服务器上，但是服务端的session的实现对客户端的cookie有依赖关系的；

4.session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能。考虑到减轻服务器性能方面，应当使用cookie。

