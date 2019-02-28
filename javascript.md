# JavaScript

#### 请用 javascript 写出 B 继承 A 的方法？

答：

1. 原型继承：

```js
var A = function() {
  this.a = 1
  this.b = 2
  this.add = function() {
    console.log(a + b)
  }
}
var B = function() {}
B.prototype = new A()
B.prototype.c = 3
B.prototype.add = function() {
  console.log(B.a + B.b + B.c)
}
var g = new B()
console.log(g.a)
console.log(g.b)
console.log(g.c)
g.add()
```

2. 构造函数继承：

```js
var A = function() {
  this.a = 1
  this.b = 2
  this.add = function() {
    console.log(a + b)
  }
}
var B = new A()
B.c = 3
B.add = function() {
  console.log(B.a + B.b + B.c)
}
var g = new B()
console.log(g.a)
console.log(g.b)
console.log(g.c)
g.add()
```

3.call,apply 继承

```js
var A = function() {
  this.a = 1
  this.b = 2
  this.add = function() {
    console.log(a + b)
  }
}
var B = function() {
  A.call(this)
  this.c = 3
  this.add = function() {
    console.log(this.a + this.b + this.c)
  }
}

var g = new B()
console.log(g.a)
console.log(g.b)
console.log(g.c)
g.add()
```

#### 请谈谈你对闭包的理解，写出一个简单的例子？

答：当在函数内部定义了其他函数时候，就创建了闭包。闭包有权访问包含函数内部的所有变量。

闭包就是做了一个传送门这个传送门分几步（四步）：

- 函数外部不能访问函数内部变量；
- 函数内部的函数可以访问函数的变量；
- 函数内部的函数如果 return 函数外部的变量；
- 那调用函数内部函数时就等于访问了函数内部的变量；

  有啥用：既然不想变量那么多暴露出来 那么把变量搞到函数里就好了。如果又想暴露一部分 那就想暴露哪个就用函数内部方法 return 哪个。

```js
function outside() {
  //定义局部变量
  var a = 1
  //内部函数
  function inside() {
    a++
    alert("a", a)
  }

  return inside()
}
outside()()
```

#### 怎么设置和获得以及删除 cookie?

cookie：存储数据，当用户访问了某个网站时，我们就通过 cookie 来向访问者电脑上存储数据。

document.cookie = '名字=值' ; 写入  
document.cookie 读（cookie 可读可写）  
每个 cookie 存放的内容大小也是有限制的，不同的浏览器不同，如果想长时间存放一个 cookie，需要设置这个 cookie 的时候，同时设置一个过期的时间。cookie 默认是历史存储的，当浏览器关闭进程的时候自动消失。

document.cookie = '名称 = 值; expires = '+时间;(时间是字符串格式的时间)

```JS
//设置
function setCookie(key,value,t){
var oDate = new Date(); //获取系统时间
oDate.setDate(oDate.getDate()+t); //根据来访者的时间来设置过期时间

//oDate为对象时间，所以需要将其转化成字符串时间 toGEMTString()
//内容最好编码存放：encodeURI();编码    decodeURI(); 解码
document.cookie = 'key = encodeURI(value); expires = '+oDate.toGMTString()
}

//setCooie('sex','男',10)

//获取
function getCookie(key){
  var arr1 = document.cookie.split(';');
  for(var i = 0; i<arr1.length; i++){
    var arr2 = arr1[i].split('=');
    if(arr2[0] == key){
      return decodeURI(arr2[1])
    }
  }
}
//getCookie(key)

//删除
function removeCookie(key){
  setCookie(key,'',-1)
}
```

#### 用JS来实现动画效果  
答：可以用定时器或者`requestAnimationFrame`（浏览器用于定时循环操作的一个接口，类似于setTimeout，主要用途是按帧对网页进行重绘。在于充分利用显示器的刷新机制，比较节省系统资源。）  
[实例](./demo/requestAnimationFrame.js)

#### 关于var重复声明的问题，看下段代码会弹出什么结果？  
```js
//问题
var a = 100;
function fn() {
    alert(a); 
    var a = 200;
    alert(a); 
}
fn();
alert(a); 
var a;
alert(a);  
var a = 300;
alert(a); 

//答案  
var a = 100;
function fn() {
    alert(a); //undefined
    var a = 200;
    alert(a); //200
}
fn();
alert(a); //100
var a; 
alert(a);  //100
var a = 300;
alert(a); //300
```

#### 一行代码实现数组去重?
```js
[...new Set([1,2,3,4,1,'a','b',3,'b'])]
```
