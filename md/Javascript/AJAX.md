# AJAX

## 概念

* Asynchronous(异步) Javascript And XML 

## 步骤

* 创建一个异步对象 var xhr = new XMLHttpRequst()
* 打开一个url地址 xhr.open(请求方式:"get"/"post","url:请求文件的路径",true?false(是否异步))
* 绑定onreadystatechange事件成功返回并携带数据
* xhr.readyState === 4 && xhr.status === 200, 说明成功
* xhr.send(null)发送给后台,向后台传数据