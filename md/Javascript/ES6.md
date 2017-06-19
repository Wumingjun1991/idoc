# ES6

## 定义变量

* 用let来定义变量,没有预解释,不能重复的进行声明定义
* 虽然用let定义的变量不会进行预解释,但是在代码执行之前也会先把let定义的变量过滤一遍,一旦不合法就直接报错,代码也不会执行了
* const定义静态变量,不能修改值,定义的时候必须要赋值,如果不赋值就会报错
* const在同一级作用域下是不能重复定义的,可以在不同作用域中定义

## 解构赋值

* 解构赋值可将数组的元素或对象的属性赋予给另一个变量，该变量的定义语法与数组字面量或对象字面量很相似，此语法非常简洁，相比于传统的属性访问方式，更加直观清晰
* 嵌套赋值
* 省略赋值
* 不定参数
* 默认值

## 块级作用域

* 用{}括起来的是私有作用域,块级作用域

## 函数问题

* 给函数的形参赋值和解构赋值的规律是一样的

## for-of循环

* 举例: 

```javascript
var ary = [1,2,3,4];
for (let val of ary){
    console.log(val);//val是每一项的值
}
```

* for-of循环不能用来循环对象

## 扩展运算

* 扩展运算符是三个点...,可以将一个数组直接转为非数组

```javascript
console.log(...[1, 2, 3]);
// 1 2 3  
console.log(1, ...[2, 3, 4], 5);
// 1 2 3 4 5
```

* 可以在传参数的时候使用.而且可以用在任何位置
* 可以代替apply来给函数传参数

```javascript
// ES5 的写法  
Math.max.apply(null, [14, 3, 77]);  
// ES6 的写法  
Math.max(...[14, 3, 77]);
//  等同于  
Math.max(14, 3, 77);
```

* 可用于合并数组

```javascript
var arr1 = ['a', 'b'];  
var arr2 = ['c'];  
var arr3 = ['d', 'e'];  
// ES5 的合并数组  
arr1.concat(arr2, arr3);  
// [ 'a', 'b', 'c', 'd', 'e' ]  
// ES6 的合并数组  
[...arr1, ...arr2, ...arr3]  
// [ 'a', 'b', 'c', 'd', 'e' ]  
```

* 将非数组转为数组

```javascript
[...'hello'];
// [ "h", "e", "l", "l", "o" ]
```

* 将类数组转为数组

```javascript
function to(){
    return [...arguments]
}
console.log(to(1,2,3,4,5));//[1,2,3,4,5];
```

## 箭头函数

* 箭头函数是匿名函数的一种简写方式

```javascript
let fn=a=>a;
console.log(fn(2)); // 2
let fn1 = (a,b) => a + b;
console.log(fn1(4,6)); // 10
```
```javascript
let f = x => console.log(x) + 1;
let res = f(1); // 1
console.log(res); // NaN
```

* 如果函数中有其他代码,要用大括号包起来
* 箭头函数数组中的方法的处理

```javascript
let ary = [1,3,5];
ary = ary.map(function(item,index) {
     return item + 1;
});
ary = ary.map(item => item + 1);
console.log(ary);

ary.sort((a,b) => a - b);
ary.sort((a,b) => b - a);

````

* 箭头函数字符串中的应用

```javascript
let str = '1,2,3,4,5';
str = str.replace((/(\d),/g),function() {
     return ++arguments[1]
});
str = str.replace((/\d,/g),(undefined,b)=> ++b);
```

* 当不需要传参数的时候,也要在箭头前面加一个小括号

```javascript
window.setTimeout(() => {console.log(1)},1000)
```

* 箭头函数中的this默认就是window
* 箭头函数中的this不是window的特殊情况:当箭头函数作为参数的时候,并且是在一个对象的某个属性值中,this就是这个对象
* 在DOM0级事件绑定的时候,箭头函数中的this还是window

## Symbol

* Symbol是用来定义字符串的

## ES6模板字符串

* 在字符串中有特殊意义的字符: `, $, {}
* 如果拼接字符串的时候需要用到这三个特殊意义的字符,必须用\进行转义,转义符本身如果有需求也要用\转译
* 在拼接字符串中插入变量: `${变量}`
* 插入表达式,和插入变量的方式一样

```javascript
function fn(x,y) {
    return x + y;
};
let str = `1 + 2 = ${fn(1,2)}`
```

* 在拼接字符串的时候,如果${}里面的是数组或者对象的话,会默认的调用toString()方法进行数据转换

```javascript
let str = `${[1,2]}`;
console.log(str); // 输出结果是字符串'1,2'
```
