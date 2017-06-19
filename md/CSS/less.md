# less

> less也是用来写样式的,和css效果一样,都是实现样式的写法,只是语法不一样,它涵盖了一些JS的思想

## 定义变量

* less中有变量的概念,可以通过@来定义一个变量
* 还可以以变量的名定义定义为变量

```less
@word:'hello';
@c: #ff5700;
@var: 'word'; // 定义了一个变量var赋值为一个变量名word
@col: 'c';    // 定义了一个变量名col赋值为一个变量名c
div{
   content: @@var;// 如果想要引用值本身为变量名的变量,就要用两个'@@'
}
```

## 混合类

* 在less中我们可以定义一些通用的属性集为一个选择器，然后在另一个选择器中去调用这些属性. 例如：

```less
.class1{
    font-size: 20px;
    width: 200px;
    height: 50px;
    border: 1px solid red;
}
.box1{
    .class1;
    background-color: #0000ff;
}
```

* 带参数混合: 在less中可以像JS函数一样定义一个带参数的属性集合

```less
.radius(@rad){
    border-radius: @rad;
    -webkit-border-radius: @rad;
    -moz-border-radius: @rad;
    -ms-border-radius: @rad;
    -moz-border-radius: @rad;
}
.box1{
    .radius(10px);
    border:1px solid springgreen;
}
```

* 给参数赋值默认值:

```less
.font(@size:18px){
    font-size: @size;
}
.menu li{
    .font();
}
```

* less的参数集合中也有一个arguments的属性,它包含了所有传入的参数
```less
.bor(@x, @y, @z) {
    border: @arguments;
}
.wh(@w:100px, @h:30px) {
    width: @w;
    height: @h;
}
.menu li {
    .wh(200px);
    .bor(3px,solid,yellow );
}
```

## 匹配模式和引导表达式

*　匹配模式:

```less
.min(drak,@color){
    color:draken(@color,20%);
    // 将颜色加深20%
}
.min(light,@color){
    color: lighten(@color,20%);
    // 将颜色变浅20%
}
.min(@_@color){ // @_ 接收任意值,不管传入的是什么,它都会执行
    display: block;
}
@switch1:drak;
@switch2:light;
span{
    .min(@switch1,#ddd)
}
```

## color函数

* 颜色加深 lighten(@color,10%): return a color which is 10% lighter than @color
* 颜色变浅 darken(@color,10%): return a color which is 10% draker than @color
* 增加饱和度 statuate(@color,10%): return a color which is 10% statuated than @color
* 减少饱和度(褪色) destatuste(@color,10%)
* fadein(@color,10%)
* fadeout(@color,10%)
* fade(@color,10%)
* spin(@color,10%)
* spin(@color,-10%)
* 混合 mix(@color1,@color2)

## 提取颜色信息

* hue(@color): 返回当前颜色的色调
* staturation(@color): 返回当前颜色的饱和度
* lightness(@color): 返回当前颜色的亮度(浅的度数)
* old:
* new: 