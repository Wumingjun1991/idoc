# DOM

## 获取DOM元素

* [上下文].getElementById("元素的ID"); 通过ID名获取元素,一般浏览器中一个页面相同的ID只有一个,所以获取出来的是一个元素,但是以后可能或遇到有相同的情况,这样获取出来的是第一个,所以要求我们起名的时候相同的ID只能是一个
* 注意:**通过ID获取元素,上下文只能是document**
* [上下文].getElementsByName("name名字"); 通过name获取一组元素(类数组,length,索引),这个方法的上下文也只能是document
* 在IE下,name作用和ID一样,所以name和ID不能一样,而且只有input的name才有效而其他的识别不出来
* [上下文].getElementsByClassName("class名字"); 通过classname获取一组元素(类数组,length,索引)上下文自己定义,一般都是父级元素,最多不会超过三级
* [上下文].getElementsByTagName("标签名字"); 通过标签名获取一组元素(类数组,length,索引)上下文自己定义,一般都是父级元素,最多不会超过三级
* innerHTML: 给元素添加或者修改内容,可以识别标签,获取的时候所有内容(包括标签)都会获取出来
* innerText: 给元素添加或者修改内容,不能识别标签,获取的时候只会获取文本内容

## 获取元素的样式

* 元素(对象)有个内置属性叫style,style属性也是一个对象,它有很多样式属性
* 元素.style.color; 获取这个元素中的颜色属性
* 注意:**style只能获取行内样式(不常用),添加的样式也是加在行内(常用)**
* getComputedstyle(元素).样式属性: 获取该元素所有的样式**只能获取不能修改**
* getComputedstyle这个方法IE678不兼容,IE有自己的方法:currentstyle

## DOM元素的增删改查

* 获取的元素.className=" ", 给该元素增加一个类名,如果这个元素本身就有类名,则覆盖这个类名
* 获取的元素.className+=" ", 给元素增加新的类名,不覆盖原有类名