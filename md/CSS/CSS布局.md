# CSS布局

## 固定布局

* PC端使用

## 媒体查询

* 媒体查询是指通过一定的语法,查询浏览器可视区域的宽度或者高度,通过区分宽高来进行同一个html文件多个css样式的添加
* 先写默认样式的css代码,再写需要查询时的css代码

```javascript
 <style>
        div {
            height: 300px;
            background-color: greenyellow;
        }

        @media screen and (max-width: 500px) {
            div {
                height: 600px;
                background-color: pink;
            }

        }
    </style>
```

* 通过link元素查询媒体的宽度和高度,可以切换不同的css文件

```javascript
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.css">
```

* 结合CSS媒体查询,可以创建适应不同设备的方向(横屏landscape、竖屏portrait等)的布局
* 语法:orientation：portrait | landscape
* portrait：指定输出设备中的页面可见区域高度大于或等于宽度
* landscape： 除portrait值情况外，都是landscape
* 实例：

```javascript

  @media only screen and (orientation: landscape) {
      body {
          background-color: lightblue;
      }
  }

```

## 百分比布局

## 弹性盒模型布局

## rem布局

* 通过计算根元素的字体大小与设计稿还有视口宽度(只用于移动端)
* 一般设计师给的移动端设计稿大小是640px
* rem布局对于字体的大小控制不是特别完美,所以有时候页面中字体部分我们可能还会通过px来进行控制(媒体查询配合)
* 移动端布局时,一般会给最外面的盒子设置一个最大宽度640px,并且设置一个最小宽度320px
* rem计算公式:(设备的宽度/设计稿宽度*100),这个100可以乘可以不乘,但是建议乘,因为谷歌浏览器不支持font-size<12px
* rem布局的时候,图片需要进行控制,背景图片也要控制

### 常用移动设备屏幕宽度

* iphone5:320px
* iphone6:375px
* iPhone6p:414px