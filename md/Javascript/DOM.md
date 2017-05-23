# DOM

## DOM基本知识

* DOM可以操作元素以及元素的内容,标签属性,文字,音视频等等(只要是直接写在文档中的,DOM都可以直接操作)
* DOM可以描述每个元素之间的关系图谱

## 获取DOM元素

### 上下文

* 就是限定当前获取元素的范围

### 通过ID获取元素

* [上下文].getElementById("元素的ID"); 通过ID名获取元素,一般浏览器中一个页面相同的ID只有一个,所以获取出来的是一个元素,但是以后可能或遇到有相同的情况,这样获取出来的是第一个,所以要求我们起名的时候相同的ID只能是一个
* 如果这个方法没有获取到元素,返回的结果是null
* 可以直接用元素的ID来代表当前的这个元素(不推荐)
* 如果一个页面中有多个id名称相同的元素,只获取第一个元素
* 在IE6,7中,会把表单元素(input)的name属性值当作ID来使用,所以name和ID不能一样,而且只有input的name才有效而其他的识别不出来
* 在IE6,7中,不区分ID的大小写
* 在项目中,不要让表单元素的name和其他元素的ID重复,也不要用ID的大小写来区分不同的元素
* 注意:**通过ID获取元素,上下文只能是document**

### 通过选择器获取元素

* [上下文].querySelector('value');通过选择器获取元素,传入的value值和css选择器相同,可以写类,id,标签,后代选择器,子级选择器
* [上下文].querySelectorAll('value');获取这个名称的所有元素
* IE低版本浏览器不兼容

### 通过name属性的值获取元素
 
* [上下文].getElementsByName("name名字"); 通过name获取一组元素(类数组,length,索引),这个方法的上下文也只能是document
* 在IE浏览器下,只对表单元素起作用,这个方法应用于获取具有同样name的表单元素

### 通过类名获取元素

* [上下文].getElementsByClassName("class名字"); 通过元素的类名获取一组元素,上下文自己定义,一般都是父级元素,最多不会超过三级
* 获取的是一个对象数据类型结果,并且是一个类数组(以数字作为索引,索引从0开始,逐级递增,索引代表的是当前对应的某一个元素,有一个length的属性,代表获取的元素个数)
* 在IE67中元素身上没有这个属性或方法
* 获取这一组数据中的某一个元素: oDivs[i]/oDivs.item(i)

### 通过标签名获取元素

* [上下文].getElementsByTagName("标签名字"); 通过标签名获取一组元素(类数组,length,索引)上下文自己定义,一般都是父级元素,最多不会超过三级

### 获取文档的根元素

* document.documentElement

### 获取body元素

* document.body

### 其他方式

* innerHTML: 给元素添加或者修改内容,可以识别标签,获取的时候所有内容(包括标签)都会获取出来
* innerText: 给元素添加或者修改内容,不能识别标签,获取的时候只会获取文本内容

## DOM节点

* 元素节点: nodeName: 大写标签名; nodeType: 1; nodeValue: null
* 文本节点: nodeName: #text; nodeType: 3; nodeValue: 文本内容
* 注释节点: nodeName: #comment; nodeType: 8; nodeValue: 注释内容
* document: nodeName: #document; nodeType: 9; nodeValue: null
* 在HTML中所有东西都是节点

## DOM节点操作方法

* Node 在页面中出现的所有的东西都是节点,元素,注释,文本等都是节点
* 获取指定元素下所有的子节点: xxx.childNodes
* 获取指定元素下所有的元素子节点:xxx.children **不兼容低版本浏览器**
* 获取指定元素的父节点: xxx.parentNode;返回值是一个元素
* 获取指定元素的上一个节点: xxx.previousSibling
* 获取指定元素的上一个元素节点: xxx.previousElementSibling **不兼容低版本浏览器**
* 获取指定元素的下一个节点: xxx.nextSibling
* 获取指定元素的下一个元素节点: xxx.nextElementSibling **不兼容低版本浏览器**
* 获取指定元素下的第一个节点: xxx.firstChild
* 获取指定元素下的第一个元素节点: xxx.firstElementChild
* 获取指定元素下的最后一个节点: xxx.lastChild
* 获取指定元素下的最后一个元素节点: xxxlastElementsChild

## 获取元素的样式

* 元素(对象)有个内置属性叫style,style属性也是一个对象,它有很多样式属性
* 元素.style.color; 获取这个元素中的颜色属性
* 注意:**style只能获取行内样式(不常用),添加的样式也是加在行内(常用)**
* getComputedstyle(元素).样式属性: 获取该元素所有的样式**只能获取不能修改**
* getComputedstyle这个方法IE678不兼容,IE有自己的方法:currentstyle

## DOM元素的增删改查

* 创建新的元素节点: createElement()
* 向指定元素所有内容之后添加一个元素节点: 父级对象.appendChild(新创建的节点)
* 向指定元素之前添加新创建的元素节点: parent.insertBefore(new,old)
* 删除创建的元素节点: parent.removeChild(要删除的节点)
* 克隆一份节点: 要克隆的节点.cloneNode(true/false/不添加内容)
* true: 将这个元素以及里面所有内容都克隆一份
* false或者什么都不加: 只克隆当前元素,里面的内容不会复制
* 替换节点: parent.replaceChild(替换的元素对象,被替换的元素对象)
* 创建属性节点: setAttribute ('属性名','属性值')会添加到元素的开始标签内
* 获取属性节点: getAttribute('属性名')
* 删除属性节点: removeAttribute('属性名')
* 获取的元素.className=" ", 给该元素增加一个类名,如果这个元素本身就有类名,则覆盖这个类名
* 获取的元素.className+=" ", 给元素增加新的类名,不覆盖原有类名