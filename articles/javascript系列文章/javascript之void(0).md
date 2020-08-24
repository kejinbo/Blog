# javascript 之 void(0)

> `void`运算符对给定的表达式进行求值，然后返回 `undefined`。

先前看[underscore](https://underscorejs.bootcss.com/docs/underscore.html)的源码，里面有个判断是这样写的:

```js
if(context === void 0) return func;
```

当时第一次看到有点懵，竟然还有这种操作，恕我孤陋寡闻。后来查阅了[文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/void)才发现，原来`void 0`写法等价于`undefined`，即上面的代码等价于：

```js
if(context === undefined) return func;
```

文档描述中指出：void 运算符通常只能用于获取 `undefined`的原始值，一般使用 `void(0)`（等同于`void 0`）。在上述情况中，也可以使用全局变量 `undefined` 来代替（假定其仍是默认值）。为什么说假设仍是默认值呢？我们下面分析一下

## void(0) vs undefined

我们先看下undefined的文档说明

> undefined是js原始类型值之一，也是全局对象window的属性，在部分低级别的浏览器（IE7,IE8）中可以被修改，在局部作用域中也可以被修改。

```js
var undefined = '111'
console.log(undefined) //111

在旧版的IE中直接改写了undefined。
```

也就是说当你想知道一个变量是不是等于undefined的时候，直接判断就不安全了。

接下来我们在看一段js

```js
var testUndefined = function(){
  var obj = {}
  var undefined = 'underscore'
  var window = {
    'undefined': 'bb'
  }
  console.log(window) //{'undefined': 'bb'}
  console.log(undefined) //underscore
  console.log(window.undefined) //bb
  console.log(obj.name === undefined) // false
  console.log(obj.name === window.undefined) // false
  console.log(obj.name === (void 0)) // true
}
testUndefined()
```

从上面的代码中可以看出，window,undefined本身在局部作用域中是可以被修改的。这样将导致判断undefined是有风险的。

## 为什么要用void 0 来代替undefined

> 通过上述栗子可以看出。在某些情况下用全局的undefined判断是有风险的。因为他可能会被修改过。而`void 0`在任何情况下返回的都是`undefined`，同时兼容性上所有浏览器都是支持的。
