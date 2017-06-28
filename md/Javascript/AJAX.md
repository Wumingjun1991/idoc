# AJAX

## 概念

* Asynchronous(异步) Javascript And XML 
* 异步: 客户端和服务器的数据交互,不需要将整个页面刷新,只需要将操作的这一部分更新一下,这就是局部刷新
* AJAX一般都是用来请求页面的部分数据,再将获取出来的数据绑定到页面的指定位置

## 请求步骤

* **第一步,创建AJAX对象**
* 创建一个异步对象 var xhr = new XMLHttpRequst(),这个方法不兼容IE6及更低版本的浏览器,需要做兼容处理
* **第二步,打开请求接口请求数据**
* 打开一个url地址 xhr.open([请求方式],[API接口],[设置同步异步],[User name],[User Pass]);
* [请求方式]:get系列(GET/DELETE/HEAD),post系列(POST/PUT))
* [User name]: 用户名
* [User Pass]: 用户密码
* 有些服务器为了安全考虑,只允许部分人可以访问,只有分配到权限的这部分人才能访问,访问的时候需要提供安全密钥,一般的服务器是不需要这么麻烦,匿名访问就可以,所以只需要传前三个参数即可
* **第三步,监听不同的状态进行不同的业务操作**
* xhr.readyState: AJAX状态,有0~4这五个值
* 0: unSend 未发送,刚开始创建一个AJAX实例 var xhr = new XMLHttpRequst(); 
* 1: opened 已经打开,第二步open('get',url,true)
* 2: headers_received 客户端已经收到服务器的响应头了
* 3: loading 服务器返回的响应主体正在传输
* 4: done 服务器返回的响应主体已经被客户端接收
* xhr.status: HTTP状态码,通过这个状态码可以知道这个HTTP事物是否成功以及失败的原因
* 以2开头: 只要是以2开头的就代表成功
* 200: OK
* 以3开头: 也代表成功,但是这个过程经过了特殊处理
* 301: Moved Permanently 在新版的HTTP协议中代表永久重定向,比如访问http:\\www.360buy.com默认就会跳转到https:\\www.jd.com
* 302: Moved Temporarily 在新版的HTTP协议中代表临时重定向(服务器的负载均衡)
* 304: Not Modified 获取的是浏览器缓存中的数据(网站性能优化的重要手段,一般都会将一些不怎么变的静态资源JS/CSS/IMG等做成304缓存,再次访问的时候可以直接从缓存中获取这些数据,不用向服务器重新请求数据,提高了网页的加载速度)
* 以4开头: 代表了错误,而且是客户端的错误
* 400: Bad Request 请求参数错了
* 401: Unauthorized 无访问权限
* 403: Forbidden 请求接收了,但是没有返回正常的结果,没有原因
* 404: Not found 请求的地址不存在
* 413: 客户端传给服务器的内容超过了服务器愿意接收的范围
* 以5开头: 代表服务器错误
* 500: Internal Server Error 服务器的未知错误
* 503: Server Unavailable 服务器超负荷
* xhr.readyState === 4 && xhr.status === 200,当这两个值分别是4和200的时候,说明请求成功
* xhr.response: 获取响应主体(一般不用)
* xhr.responseText: 获取响应主体内容,是text(字符串)格式的
* xhr.responseXML: 获取响应主体内容,是XML格式(XML文档)
* xhr.getResponseHeader("Data"): 获取响应头的指定内容
* Xhr.getALLResponseHeaders: 获取所有的响应头
* xhr.timeout: 设置请求的超时时间,比如设置的是3s,超过3s就算是请求失败,并且如果请求超时就会触发ontimeout事件
* xhr.abort(): 中断当前AJAX请求,一旦中断请求就会触发onabort事件
* xhr.setRequestHeader([key],[value]): 设置请求头信息
* **第四步,向服务器发送请求数据**
* 发送send(),AJAX这件事是从send开始的,之前都是在做准备工作,当"xhr.readyState==4"的时候结束
* xhr.send(null)发送给后台,向后台传数据

## 数据的异步加载

* 先把两屏的数据加载出来,后面的数据不进行处理,当页面滚动到对应区域的时候再重新请求数据然后绑定渲染数据

## 网站性能优化

* 减少HTTP请求
* CSS/JS文件进行合并
* ICON图片进行合并(雪碧图/css sprite)
* 图片延迟加载
* 数据的异步加载
* 在移动端,如果页面是一个简单的宣传页,尽量把JS和CSS写成内嵌式

## 面试问题

* get系列和post系列有什么区别
* 1.传参数方式不同
    * get: 通过URL+?+参数
    * xhr.open('get','/userInfo?name=xxx&age=100')
    * xhr.send(null)
    * post: 请求主体
    * xhr.open('post','/userInfo');
    * xhr.send('name=xxx&age=100&sex=1');
* 2.get容易出现缓存,而post不会
    * 原因: get是通过URL加上问号拼接参数的方式传给服务器数据的,如果当前传的参数和上一次一样了,浏览器就会走它的记忆功能(缓存),以为请求的是同一个URL,会把之前的返回,但是不是有些需求是需要获取实时信息的,例如股票信息等等
    * 解决方法: 保证每次请求的URL都不一样,可以给每个UR后面拼接一个变量,随机数或者是时间戳
    * xhr.open('get','/userInfo?name=xxx&age=100&_='+Math.random());
    * xhr.open('get','/userInfo?name=xxx&age=100&_='+(new Data).getTime());
* 3.参数大小的限制
    * get: get请求是把数据放在url上,但是浏览器的url大小是有限制的,如果超过大小限制浏览器就会默认截断(不同浏览器是不一样的:谷歌是8KB,火狐是7KB,IE大约是2KB)
    * post: 数据在请求主体中,大小没有限制,但是在真实项目中为了保证上传速度,一般会限制在100KB以内
* 4.安全性
    * get: get请求是将数据放在URL上,所有数据都能被看到,所以安全性不能保证
    * post: 请求数据都在请求主体中,一般重要的信息都是用post请求
    
## AJAX兼容处理

* IE6及以下版本不兼容'var xhr = new XMLHttpRequest;'这种方式
* 在IE6及以下版本浏览器中有三种方式:
    * xhr=new ActiveXobject('Microsoft.XMLHTTP');
    * xhr=new ActiveXobject('Msxml2.XMLHTTP');
    * xhr=new ActiveXobject('Msxml3.XMLHTTP');
* AJAX兼容处理:

```javascript
function createXHR(){
    var xhr = null;
    if (window.XMLHttpRequest){
        xhr = new XMLHttpRequest();
    }else{
        try {
            xhr = new ActiveXobject('Microsoft.XMLHTTP');
        }catch (e){
            try{
                xhr = new ActiveXobject('Msxml2.XMLHTTP');
            }catch (e){
                xhr = new ActiveXobject('Msxml3.XMLHTTP');
            }
        }
    }
}
// 这个方法可以解决兼容,但是每一次执行createXHR都需要重新验证当前浏览器支持哪个方法,耗费性能,还可以用惰性思想解决这个问题,只运行一次,如果还有AJAX请求则直接使用正确方式而不用再次判断
function creatXHR(){
    var xhr = null,
        ary = [
            function() {
                 return new XMLHttpRequest;
            },
            function() {
                 return new ActiveXobject('Microsoft.XMLHTTP');
            },
            function() {
                 return new ActiveXobject('Msxml2.XMLHTTP');
            },
            function() {
                 return new ActiveXobject('Msxml3.XMLHTTP');
            },
        ];
    // 循环数组ary中的每一项,依次执行
    for(var i = 0; i < ary.length; i++){
        try{
            xhr = ary[i]();
            createXHR = ary[i];
            break;
        }catch(e){}
    }
    return xhr;
}
```
