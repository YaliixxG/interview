# JavaScript

_请用 javascript 写出 B 继承 A 的方法？_

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
