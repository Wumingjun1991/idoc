# fs

> fs模块是Node.js内置的模块,是文件系统模块,负责读写文件,这里面提供了同步和异步的方法
> 参考网址: http://www.jianshu.com/p/5683c8a93511

## 读取文件

```javascript
// 第一个参数是文件名,就是要被读取的文件
// 第二个参数是可选参数，可指定flag（文件操作选项，如r+ 读写；w+ 读写，文件不存在则创建）及编码格式,这个参数是以对象的形式传入的
// 第三个参数是回调函数,会默认给这个函数传两个参数err(错误信息)和data(读取的数据)
fs.readFile('/test.txt', {flag: 'r+', encoding: 'utf8'}, function (err, data) {
    if(err) {
     console.error(err);
     return;
    }
    console.log(data);
});

```

## 写入文件

> 写入文件会清空文件中的原有数据 

```javascript
// 第一个参数是要写入文件的文件名
// 第二个参数是写入的数据,可以是字符串也可以是Buffer
// 第三个参数,可选参数,可以传入编码格式,文件的读写权限等等,也是以对象的形式传入的
// 第四个参数是回调函数,会默认给这个函数传两个参数err(错误信息)和data(读取的数据)
fs.writeFile('/test.txt', data, {flag: 'a'}, function (err) {
   if(err) {
    console.error(err);
    } else {
       console.log('写入成功');
    }
});

```

## 以追加的形式写入文件

```javascript
fs.appendFile('/test.txt', function () {
  console.log('追加内容完成');
});
```

