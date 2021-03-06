# HTML

## HTML基本知识

### 前端三层
 * HTML结构 是被浏览器直接解析加载的
 * CSS样式 是在html结构之间去装点网站
 * javascript交互 动态效果/数据交互
 
### 网页
 
* 网页是构成网站的基本元素，通俗来讲一个html文件就是一个网页
 
### 网站
 
* 是由很多个网页组成，共同为一个目标服务的网页集合

### 站群(流水线统一化管理)

* 由很多个网站组成的，为同一个公司服务
* 例如整个百度下所属的子公司都有自己的网站，百度搜索，糯米，音乐，贴吧，百度金融....

### HTTP(超文本传输协议)

* **HyperText Transfer Protocol**
* 在万维网上提供一种发布和接收HTML页面(网页)的方法
* eg:http://www.zhufengpeixun.cn
* 404: 服务器无响应
* 步骤：
  * 建立连接：输入网址，建立客户端和服务器端的连接
  * 发送请求信息：客户端发送给一个请求给服务器
  * 发送响应信息：服务器接到请求后，给予相应的响应信息
  * 关闭连接：客户端接收服务器所返回的信息通过浏览器显示在用户的显示器上，然后客户机与服务器断开连接

### URL(统一资源定位器)

* **Uniform Resource Locator**
* 用于定位万维网上的文档
* URL也被成为网址，可以由单词组成，或者是IP地址

### 服务器

* 服务器是提供算服务的设备，由于服务器需要响应服务请求，并进行处理，因此一般来说服务器应具备承担服务并且保障服务的能力
* 在网络环境下，根据服务器提供的服务类型不同，分为文件服务器，数据库服务器，应用程序服务器，WEB服务器等
* 防篡改：web端服务器一旦受到攻击，在0.0n秒做出反应，将内网服务器中的内容，马上覆盖在web端服务器上
* 负载均衡：平均web服务器压力，将用户访问进行分流
* VPN：用来翻墙，有指定帐号就可以通过这个产品进行内网访问

### 浏览器

* 浏览器是指可以显示网页服务器或者文件系统HTML文件(标准通用标记语言的一个应用)内容，并让用户与这些文件交互的一种软件
* 浏览器按照内核不同分类：IE(Trident核心)，谷歌(WebKit核心)，火狐(Gecko核心)，欧朋(Presto核心)
* IE6-->IE7(很快淘汰)-->IE8(时间较长，稳定性好)-->IE9(半年到一年)-->IE10-->IE(Edge)
* 最好用的浏览器：谷歌

### 网页的基本组成

* HTML：是网页的骨架，支撑起血肉(文字，图片，音视频....)
* CSS：表皮和衣服，化妆品
* javascript：动态和交互

### HTML(超文本标记语言)

* 网页文件本身是一种文本文件，只有通过特定的标记描述，那些普通文本才能在浏览器中正常的显示，在页面中如果遇到图片，音视频的时候如何用文本描述，需要用超文本进行引入才能正常显示

### HTML的特点

* 浏览器根据标记来解析和描述内容(从html的第一行向下解析)，如果遇到错误，浏览器不会指出，也不会报错，会跳过此处继续加载，编辑人员需要根据显示效果分析哪里出了错误--html不会报错

### HTML的兼容问题

* 因为浏览器是由不同厂商生产的，所以对html的解析有分歧，产生了页面效果显示不一致的情况，我们将这个问题叫做兼容问题

## HTML标签

### 标签语法

* 由成对的尖括号和关键字组成的超文本，叫做标签`<tagName>`
* 关键字(标签名)：是已经规范过的，不是自己随便制造的，在编辑html这门语言的时候，相关组织将这些文本归纳到了一定的规则中，使他有了特殊的含义和作用
* 例如：

 ```
 <div>
 </h2>
 <img />
 ```
 
### 标签属性
 
  * 属性提供了有关HTML元素的更多信息 
  * 语法：由属性名和属性值组成(键值对 key='value')
  * 标签属性是用来描述标签功能的，一般写在开始标签中，跟在标签名的后面，用空格隔开
  
  ```
  <span style="foont-family:宋体;"title="标题">
  span 是标签
  style 是标签属性名
  "font-family:宋体;"  标签属性值
  ```
  
  * 一个标签可以有很多标签属性，每一个属性之间用空格隔开
  * 标签不区分大小写，但是推荐使用小写
  * 标签属性经过html的进化，舍弃了有关样式的标签属性，保留功能的标签属性
  * 例如舍弃 width bgcolor align 这些样式描述都放在css里面
  * 保留 alt title src href...
  
### 标签的分类
  
  * 开始标签 `<div>`
  * 结束标签 `</div>`
  * 自闭合标签(空标签) `<br />` `<img />` `<hr />`
  
> 注意：只有闭合标签（由开始标签和结束标签组成，成对出现）中才可以承载和嵌套内容
  
  
## HTML元素

> 可以将元素理解为一个容器，容器中放的就是我们网页中的主要内容(内容可以为空)，
  由标签和内容组成的，叫做元素
  
```
  <div>此处是内容</div>
```
  
  
### 元素分类
  
 * 由开始标签和结束标签组成的元素，可以进行嵌套(一个元素包着另一个元素)，元素中可以添加内容
 * 空标签，只能进行功能的添加，例如 img 元素，用来引入图片，br 用来进行换行
 
 ```
 <div>content</div> -->div元素
 <img scr="url" alt="备注" /> -->img元素
 ```
  
> 标签和元素是用来标记和描述内容的，所以这些标签和元素用户是看不到的，用户只能看到这个元素中的内容
  
### 常用的html元素
  
  * 块级元素：
  
  
  | 标签名   |   描述   |
  | :-------| :-------|
  | div     |  无意义标签，用来区分网页大模块，例如网页头部，主体，内容，尾部 |
  | h1~h6    | 标题标签 |
  | p       | 段落 |
  | ul      | 无序列表 |
  | ol      | 有序列表 |
  | hr      | 水平分隔线  |
  | menu    | 菜单列表    |
  | li      | 列表项    |
  | dl      | 定义列表    |
  | dt      | 定义术语    | 
  | dd      | 定义描述    |
  | table   | 表格       |
  | p       | 段落       |
  | form    | 交互表单   |
  
  >  块级元素是指本身属性为display:block;的元素,因为它自身的特点,我们通常使用块级元素来进行大布局（大结构）的搭建
   
 * 块级元素特点：
   * 独占一行，每个块级元素都会从新的一行重新开始，从上到下排布
   * 可以直接控制宽度，高度以及盒子模型的相关css属性
   * 在不设置宽度的情况下，块级元素的宽度是它父级元素内容的宽度
   * 在不设置高度的情况下，块级元素的高度就是它本身的高度
  
 * 内联元素：
 
 
  | 标签名   | 描述         |
  | :-------| :--------------|
  | span    | 常用内联容器，定义文本内块区  |
  | a       | 超链接 锚点    |
  | b       | 加粗       |
  | strong  | 加粗强调    |
  | i       | 斜体        |
  | em      | 斜体强调     |
  | s       | 中划线(不推荐使用) |
  | strike  | 中划线    |
  | del     | 文档中已被删除的文本 |
  | br      | 强制换行      |
  | u       | 下划线    |
  | textarea | 多行文本输入框 |
  | input   | 输入框     |
  | select  | 下拉列表   |
  | lable   | input 元素定义标注（标记） |
  | img     | 引入图片   |
  | sub     | 下标      |
  | sup     | 上标      |
  | big     | 大字体文本  |
  | small   | 小字体文本   |
  
  
> 内联元素是指本身属性为display:inline;的元素，因为它自身的特点,我们通常使用内联元素来进行文字,小图标（小结构）的搭建
  
* 内联元素的特点： 
    * 和其他内联元素从左到右在行显示
    * 不能直接控制高度，宽度以及盒子模型的相关css属性，但是直接设置内外边距的左右值是可以的
    * 内联元素的宽度是由本身内容的大小决定的（文字，图片等等）
    * 内联元素只能容纳文本或者其他内联元素（此处请注意，不要在内联元素中嵌套块级元素）
  
### 表格
  
* dl用于定义列表，常用在新闻标题
* table 表格
   * caption 标题
   * thead 表头
      * tr>th (标题单元格)
   * tfoot 表尾
      * tr>td (普通单元格)
   * tbody 表身
      * tr>td (普通单元格)
* thead和tfoot分别有一个，tbody可以有很多个
* tfoot一般放置在thead后面，为了防止tbody中的内容过多，tfoot加载过慢的情况，虽然书写位置是在前面，但是在页面显示的时候，这部分依然在整个表格的最后面
* 如果table用来搭建结构，只需要写tr和td 
   
### 表单

* 一般用于获取用户信息

```
<form>
    <input type="radio" name="ok"checked="checked"><lable>描述表单元素功能</lable>(单选)
    <input type="checkbox"checked>(多选)
    <textarea maxlengh="字符输入最大值"minlenght="1"></textarea>(文本域)
    <lable>文本输入</lable><input type="text">
    <lable>密码输入</lable><input type="password">
 </form>
 ```
 
* type用来选择类型
* name="ok" 单选中的共同点，用来实现单选功能
* checked 默认选项

## HTML基本结构

> 一个html文件也叫做一个网页，可以称作是一个文档(document)，整个文档从html元素开始，一直向下分支延伸，像一颗大树一样，所以我们将html元素叫做这个文档的**根元素**

### 文档声明

* `<!DOCTYPE html>`
* 定义这个文档声明，浏览器先识别这句话，会按照定义的类型去解析这个文档
* 所有高版本都会向下兼容，所以在以后的工作中，我们直接将文档声明写成html5的就可以
* 文档声明必须写在html文件的第一行
* 文档声明不区分大小写
* 如果html文件没有文档声明，会触发浏览器的怪异模式
* 文档声明不是一个html标签

### html元素

* 此元素可告知浏览器其自身是一个HTML文档，是由开始和结束标签组成的，html文件里面所有的内容都会放在这个元素中

### head元素

* 整个文档的头部，head元素自带隐藏功能，display:none；里面的内容不会隐藏，只不过一般放置在head元素中的其他元素和内容也是自带隐藏功能的，例如link meat....

### `<meta>`规定了html文档的元信息

* `<meta>`标签应该放在head元素的第一行
* utf-8 国际通用编码
* name="keywords" content="HTML5.JS...."
* 关键字SEO优化搜索引擎

### title元素

* html文档元素的名称，一个页面就只有一个title元素，里面内容显示在浏览器的页卡位置
* title中的内容也会被SEO抓取

### link

* `<link href="favicon.ico" type="image/x-icon"rel="shortcut icon">`
 * 页卡小图标，让设计师生成
 * 一般这个图标放在整个项目的根目录下
 * 显示在页卡位置，title内容之前
 
* `<link rel="stylesheet" href="url" type="text/css">`
  * 引入一个外部css文件
  * rel不能缺少 stylesheet样式表
  * type可以省略但是建议写全

### body元素

* 定义整个文档的主体部分，所有展示给用户的内容，都在这个元素
* body中有常用的html元素(div ul)，文本内容，音频，视频，图片，表单....

## 标签语义化

* 合理的标签做合理的事情
* 浏览器会按照每一个标签的意义，去解析这个标签中的内容
* h1-->这是一个大标题，意义很重要，搜索引擎会重点抓取这里面的内容
* p-->段落，浏览器在展现这部分内容的时候，会独立成一块，让网页结构更加清晰，给用户更好的浏览体验
* 作用：
  * 重要的内容要放在语义重要的标签中，有利于SEO优化(搜索引擎抓取)
  * 在没有css样式的时候，页面也可以整齐的显示效果
  * 利于团队协作和后期维护
* 在日常工作中如何遵循标签语义化：
  * 尽量减少使用无意义标签，例如div和span
  * 尽量不使用标签和本身的css样式，例如b，font，s等标签，如果需要这些样式，那么使用css样式来进行添加
  * 在需要强调的部分，使用strong，em，但是样式尽量使用css样式来描述
  * 表格搭建时，使用`<thead>表格头部</thead>` `<tbody>表格身体</tbody>` `<tfoot>表格尾部</tfoot>`
  * 列表搭建时，使用`<ul>无序列表</ul>` `<ol>有序列表</ol>` `<dl>定义列表</dl>`
* 国家评比一个网站的关键点：访问量(流量，点击量)
* iframe 在引入其他文件时，必须写宽度与高度