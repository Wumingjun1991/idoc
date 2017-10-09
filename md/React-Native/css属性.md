# CSS属性

## 基本CSS属性

* 可以直接给元素设置宽/高:width/height
* 定位属性prosition只能设置relative(相对定位)和absolute(绝对定位)
* 边框宽度: borderBottomWidth(底部边框宽度) borderLeftWidth(左边边框宽度) borderRightWidth(右边边框宽度) borderTopWidth(顶部边框宽度) borderWidth(所有边框宽度)
* 边框颜色: borderBottomColor(底部边框颜色) borderLeftColor(左边边框颜色) borderRightColor(右边边框颜色) borderTopColor(顶部边框颜色) borderColor(所有边框颜色)
* 外边距: marginBottom(底部外边距) marginLeft(左边外边距) marginRight(右边外边距) marginTop(顶部外边距) marginVertical(相当于同时设置marginTop和marginBottom) marginHorizontal(相当于同时设置marginLeft和marginRight) margin(所有外边距)
* 内边距: paddingBottom(底部内边距) paddingLeft(左边内边距) paddingRight(右边内边距) paddingTop(顶部内边距) paddingVertical(相当于同时设置paddingTop和paddingBottom) paddingHorizontal(相当于同时设置paddingLeft和paddingRight) padding(所有内边距)
* 背景颜色: backgroundColor
* 边框圆角: borderTopLeftRadius(左上角圆角) borderTopRightRadius(右上角圆角) borderBottomLeftRadius(左下角圆角) borderBottomRightRadius(右下角圆角) borderRadius(所有圆角)

## flex布局

* flexDirection用于设定主轴的方向,即子view的布局方向,可以设置两个属性row(横向)和column(纵向)

* alignItems用于定义子组件在垂直方向上的对齐方式,可以设置4个值
    * flex-start:与父组件的顶部对齐
    * flex-end:与父组件的底部对齐
    * center:处于父容器的中间位置
    * stretch:竖直上填充整个容器

* justifyContent用于定义子组件在水平方向上的对齐方式,可以设置5个值
    * flex-start:伸缩项目与父容器左端靠齐
    * flex-end:与父容器右端靠齐
    * center:水平居中
    * space-between:第一个子组件位于父容器左端,最后一个子组件位于父容器最右端,然后平均分配在父容器水平方向上
    * space-around:所有子组件平均分配在父容器的水平方向上,左右都有留空隙

* alignSelf该属性用来设置单独组件的竖直对齐方式,与alignItem有点像,有五个属性可以设置
    * auto:按照自身设置的宽高来显示,如果没设置,效果跟streth一样
    * flex-start:与父容器顶部对齐
    * flex-end:与父容器底部对齐
    * center:位于垂直位置
    * streth:垂直拉伸

* flexWrap用于设置是否可换行,有两个属性可设置nowrap和wrap
    * nowrap:即使空间不够也不换行
    * wrap:空间不够的话自动换行

* flex用于设置伸缩项目的伸缩样式比例

## 字体相关属性

* color: 字体颜色
* fontFamily: 字体族
* fontSize: 字体大小
* fontStyle: 字体样式,正常,倾斜等，值为('normal', 'italic')
* fontWeight: 字体粗细,值为("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
* letterSpacing: 字符间隔
* lineHeight: 行高
* textAlign: 字体对齐方式,值为("auto", 'left', 'right', 'center', 'justify')
* textDecorationLine: 貌似没效果,字体修饰,上划线,下划线,删除线,无修饰,值为("none", 'underline', 'line-through', 'underline line-through')
* textDecorationStyle: ("solid", 'double', 'dotted', 'dashed') 貌似没效果，修饰的线的类型
* textDecorationColor: 貌似没效果，修饰的线的颜色
* writingDirection: ("auto", 'ltr', 'rtl') 没用过的属性,写作方向？从左到右？从右到左？

## 图片相关属性

* resizeMode: ('cover', 'contain', 'stretch'),contain是指无论如何图片都包含在指定区域内,假设设置的宽度高度比图片大,则图片居中显示,否则图片等比缩小显示;cover是指按实际大小进行显示,超出部分进行裁剪;stretch是指将图像进行拉伸显示
* overflow: ('visible', 'hidden') 超出部分是否显示，hidden为隐藏
* tintColor: 着色，rgb字符串类型
* opacity: 透明度

## 图像变换

* scaleX:水平方向缩放
* scaleY:垂直方向缩放
* rotation:旋转
* translateX:水平方向平移
* translateY:水平方向平移

## 阴影

* shadowColor: 阴影颜色
* shadowOffset: 阴影偏移量
* shadowOpacity: 阴影透明度
* shadowRadius: 阴影圆角