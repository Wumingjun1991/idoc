# AJAX

## 概念

* Asynchronous(异步) Javascript And XML 

## 步骤

* 创建一个异步对象 var xhr = new XMLHttpRequst()
* 打开一个url地址 xhr.open(请求方式:"get"/"post","url:请求文件的路径",true?false(是否异步))
* 绑定onreadystatechange事件成功返回并携带数据
* xhr.readyState === 4 && xhr.status === 200, 说明成功
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
