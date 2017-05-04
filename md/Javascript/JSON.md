# JSON

## JSON的概念

* JSON不是一个单独的数据类型,它只是一种特殊的数据格式
* JSON是一个对象数据类型的,是window下的一个属性,也可以理解为是一个全局变量
* 在低版本的IE下没有这个对象

## JSON和普通对象的区别

* JSON的属性名必须用双引号包起来
* 属性值为字符串的话也要用双引号包起来
* json字符串:一般从后台获取回来的数据都是json字符串

## JSON.parse()

* 将json格式的字符串转为json格式的对象
* 在IE6~7浏览器中,window下没有JSON对象,可以用eval来实现这个功能: eval("("+str+")")
* 使用eval的时候一定要手动加一个小括号
* 兼容IE6~7的方法:

```javascript
  function json(str) {
      return "JSON" in window ? JSON.parse(str) : eval("(" + str + ")");
    }
```

## JSON.stringify()

* 将json格式的对象转为json格式的字符串

## DOM映射

* 通过DOM方法获取的一个元素集合(类数组),这个集合仍然和页面的元素保持着联系,并且这个元素的集合会随着页面的元素增减而增减,即使把这个类数组转为一个数组,每个元素仍然和页面有联系,这就叫做DOM映射

## 回流

* 元素的位置发生改变(增加元素,删除元素,移动),会引起回流,让整个页面重新渲染一遍,从而造成性能的浪费

## 重绘

* 元素的样式发生改变,只会把当前的这个元素重新渲染一遍
* 在项目中能用重绘代替的就不用回流,能用一次回流就不要使用多次

## 向页面增加元素的方式

* 动态创建的方式document.createElement,一个一个的通过appendChild会造成多次回流,非常耗性能,但是它有一个好处,不会改变原来的元素(比如不会影响之前绑定的事件)
* 通过拼接字符串,最后再一次性通过innerHTML添加,这样只会引起一次回流,但是它会改变原来的元素(比如会影响之前绑定的事件)
* 文档碎片: 它就是一个容器专门来盛放DOM元素的

```javascript
   var flg = document.createDocumentFragment();  //创建容器
   for(var i = 0; i < jsonDate.length; i++){     //按需求给元素循环增加需要的属性 
       var oli = document.createElement('li');
       oli.innerHTML = jsonDate[i].content;
       oli.className = jsonDate[i].class;
       flg.appendChild(oli);                     //暂时存放在flg(DOM碎片)中,也是通过appendChild方式存进去的
   }
   news.appendChild(flg);                        //循环完之后,把整个flg放到需要添加的元素中
   flg = null;                                   //清空容器
```