# Express

> Express是一个简洁、灵活的node.js Web应用开发框架,是目前最流行的基于Node.js的Web开发框架

## 安装

* 安装之前先初始化: npm init -y 
* 安装Express: npm install express --save
* 安装的文件夹名不能和express同名

## 扩展资源地址

* 官网: http://www.expressjs.com.cn/
* github源码地址: https://github.com/expressjs/expressjs.com

## 基本路由设置

```javascript
let express = require('express');
// express是一个函数
// app本质上是一个请求监听函数,在客户端提交请求到服务器的时候执行
let app = express();
// app的方法名和http的请求方法名是一一对应的
// GET POST DELETE PUT OPTIONS HEAD
// 第一个参数是URL路径,第二个参数是请求监听函数
// 路由的匹配顺序是从上到下依次匹配,只要找到一个能匹配的路由就不会向下继续查找了,所以通配型路由放在最后
app.get('/signup',function (req,res) {
    // 在调用setHeader的时候响应头并没有发送,响应头会在第一次调用write的时候发送
    res.setHeader('Content-Type','text/html;charset=utf-8');
    res.end('注册')
});
app.get('/signin',function (req,res) {
    res.setHeader('Content-Type','text/html;charset=utf-8');
    res.end('登录')
});
// app.all代表能匹配所有的请求方式,'*'表示匹配所有路径
app.all('*',function (req,res) {
    res.setHeader('Content-Type','text/html;charset=utf-8');
    res.end('404 NotFound')
});

// 如果请求的路径没有任何一个路由能匹配,就会返回404,并返回响应体Cannot GET /xxx
// 监听8080端口,启动一个http服务器
app.listen(8080);
```

## 获取请求体中的参数

```javascript
/**
 * Created by w4995 on 2017/7/15.
 */
// 在服务器中获取请求中的参数
// 请求行: 请求方式 路径(用?隔开的两部分)路径名+查询字符串
//
let express = require('express');
let url = require('url');
let app = express();
// req res和原生的http服务器的请求响应对象是同一个,只不过增加了一些额外的自定义属性
app.get('/user',function (req,res) {
    let method = req.method;
    console.log(method);
    //let {pathname,query} = url.parse(req.url,true);
    //console.log(pathname);
    // req.paht req.query 这两个是express额外添加的
    console.log(req.path);
    console.log(req.query);
    //console.log(query);
    console.log(req.headers);
    res.end('ok')
});
let users = [
    {id:1,name:'aa'},{id:2,name:'bb'},{id:3,name:'cc'}
];
app.get('/users/:id',function (req,res) {
    // 先拿到路径参数里面的ID
    let id = req.params.id;
    let user = users.find(item=>item.id == id);
    res.setHeader('Content-Type','text/html;charset=utf-8');
    res.end(user.name)
});
app.listen(8080);
```

## 中间件

```javascript
let express = require('express');
let app = express();
// 中间件就是一个函数,每当有请求的时候就会执行
// 使用中间件函数,没有路径就意味着可以匹配所有路径,没有方法就是说可以匹配所有的方法
// 中间件和路由规则的执行顺序和代码排序是一致的
// 中间件作用:
// 1)编写一些公共的逻辑,所有路由都需要的方法,只需要写一次就行了
// 2)添加一些公用的属性和方法
// 公用属性: req.path,req.query
// 公用方法:
// send 向客户端(浏览器)发送响应体
// send和end方法一样都会结束写入响应体,一旦调用之后,就不能再次调用write或者end方法了(在send方法中会自动调用end方法)
// end只能接收字符串或者Buffer
// send可以接收任意类型(字符串,Buffer,对象,数组,数字)
// send也是通过中间件给res对象添加上去的
app.use(function (req,res,next) {
    res.setHeader('Content-Type','text/html;charset=utf-8');
    // next是一个函数,调用它的话可以让请求向下继续执行
    next()
});
// 一旦遇到匹配的路由,就一定不会再向下执行了
app.get('./home',function (req,res) {
    res.end('首页')
});
app.listen(8080);
```

## 路由中间件

* 和路由的用法是一样的,当客户端请求特定路径才会触发的函数

```javascript
let express = require('express');
let app = express();
let user = require('./routes/user');
let category = require('./routes/category');
// 现在use里传入了两个参数,第一个参数是路径前缀,第二个参数才是路由中间件
// 当客户端请求url地址 /user/signup的时候,也就是以/user开头的话,才会走user中间件
app.use('/user',user);
// 当客户端请求的地址是以/category开头的话,才会走category中间件
app.use('/category',category);
app.all('*',function (req,res) {
    // send 函数相当于end函数,是express提供的方法,比原生end方法更加强大
    res.send('404 Not Found')
});

app.listen(8080);
```

## ejs(模板引擎)

* ejs是一个简单高效的模板语言,通过数据和模板,可以生成HTML标记文本,可以说EJS是一个JavaScript库,EJS可以同时运行在客户端和服务器端,客户端安装直接引入文件即可,服务器端用npm包安装
* ejs安装: npm install ejs
* ejs语法参考网站: http://www.jianshu.com/p/67dda091fc68
* 在ejs模板中引入另外的ejs模板
```javascript
<% include public/header.ejs %>
<%=title%>
<% include public/footer.ejs %>
```

```javascript
let express = require('express');
let path = require('path');
let url = require('url');
let app = express();
// 设置模版引擎(ejs handlerbar jade)
app.set('view engine','ejs');
// 设置模板存放目录
// 如果存放模板的文件夹名称叫views,这句话可以省略不写,如果不叫views,必须提供
// path.resolve是从当前路径出发解析路径
app.set('views',path.resolve('views'));
// 设置模板的渲染方法
// 当express发现模板的文件后缀名为html的时候,会使用ejs模板进行渲染
app.engine('.html',require('ejs').__express);
app.get('/first',function (req,res) {
    // render渲染,绘制,express为请求对象res添加了一个render方法
    // 参数1放模板的相对路径,所以不要以/或者./开头,直接写文件名就行
    // 渲染就是把静态的模板和动态的数据对象进行混合生成HTML代码的过程
    // 读取模板存放根目录下的index.ejs文件内容
    // 用数据对象把模板中的内容替换掉
    // 把得到的HTML内容发送给客户端
    res.render('index.html',{title:'首页'});
});
app.get('/index',function (req,res) {
    res.render('index2',{title:'主页'})
});
// 路径只能写路径名
// 查询参数通过req.query获取
// 路径参数通过req.params获取
app.get('/use',function (req,res) {
    res.render('index3',req.query)
});
let users = [
    {id:1,name:'aa'},
    {id:2,name:'bb'},
    {id:3,name:'cc'},
];
app.get('/users',function (req,res) {
    res.render('users.html',{users:users})
});
app.listen(8080);
```

