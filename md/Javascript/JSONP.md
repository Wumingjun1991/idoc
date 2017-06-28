# JSONP

## 同源(同域)/非同源(跨域)

* 同源
    * 当前页面的URL: http://localhost:1234/index.html
    * 获取数据的URL: http://localhost:1234/getUserList
    * 这就是同源,可以使用AJAX获取数据
* 非同源
    * 当前页面的URL: http://localhost:1234/index.html
    * 获取数据的URL: http://www.baidu.com
    * 这就是非同源,不能使用AJAX获取数据
* 如何判断是否同源
    * 页面的URL地址和获取数据的URL地址进行比较
    * 看HTTP传输协议
    * 看域名
    * 端口号
    * 三个都相同就是同源,只要有一个不同就是跨域,跨域是不可以使用AJAX的
* 什么时候会用到跨域请求
    * 在A网站上需要展示B网站上的数据,这样的话需要在A网站的服务器上获取B网站服务器的数据,这就是跨域
    * 在大型项目中,访问人数也比较多的情况下一般都会用多台服务器管理,例如资源文件放在A服务器,数据放在B服务器上,A服务器从B服务器获取数据也是跨域(只要不是同一个服务器的请求都算跨域)
    * 二级域名sports.qq.com向一级域名www.qq.com获取数据也是跨域
* 跨域请求的方式
    * JSONP(最常用的方式)
    * iframe
    * postMessage
    * document.domain
    * crossDomain
    
## JSONP原理
* script标签是没有同源和非同源之分的,src中引入的JS文件既可以是自己服务器上的也可以是其他服务器上的(也可以理解为script标签可以向其他服务器发送请求,并且其他服务器可以接收到请求,把需要的内容返回给客户端)
* 除了script以外可以跨域请求数据的标签:link,img,audio,video,iframe
* JSONP原理: 利用script标签不存在跨域限制,把需要的请求数据的地址赋给src属性,这样就可以从别人服务器上获取相应的数据,然后在JS中把浏览器获取的数据得到并做后续的操作
```html
<script type="text/javascript">
    function ff(result) {
        console.log(result);
    };
    ff()
</script>
<script type="text/javascript" src="http://matchweb.sports.qq.com/kbs/hotMatchList?callback=ff"></script>
// 在这里发送了一个请求到腾讯服务器,腾讯服务器接收到请求之后就会去服务器上查找callbak的值,我们这里传的是ff
// 然后进行解析赋值'ff({"name":"aa","age":"12"})'然后把字符串返回给客户端
```
* JSONP请求方式是GET请求
