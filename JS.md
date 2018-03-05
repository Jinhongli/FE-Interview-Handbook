# JAVASCRIPT 相关问题

## 解释下事件代理

将 DOM 元素注册的时间绑定在其父元素（或者祖先元素）上。其原理是：JS 对 DOM 事件的处理包括三个阶段：**捕获**、**目标**、**冒泡**。事件从根元素捕获至目标元素，再从目标元素冒泡至根元素，即事件会经过目标元素的父元素。这样做的好处：

* 节省内存。
* 新增元素之后不需要再绑定事件。

## 解释下 JS 中`this`

首先`this`的值只与函数的调用方式有关：

* `new`方式调用，`this`是生成的实例对象。
* `call`，`apply`和`bind`调用，`this`是传入的实参。
* 如果是对象的方法调用，`this`是该对象。
* 如果是作为普通函数调用，`this`非严格模式下是全局对象，浏览器中的`window`；严格模式下是`undefined`。（因为非严格模式下函数中找不到`this`就会去全局查找变量，而全局的`this`就是全局变量本身）
* ES6 中的箭头函数没有`this`，其内的`this`是箭头函数父环境下的`this`。

如果函数的调用存在多种情况，那么上面判断方法的优先级从上倒下降低。

## 解释下原型继承

关于原型和原型继承：

1. 每个函数（除`.bind()`绑定的函数）都包含一个`prototype`属性，指向其原型。
2. 所有的对象均具有一个内部`[[Prototype]]`属性，指向生成该对象的构造函数的原型，又称为该对象的原型对象。（浏览器中可以通过`__proto__`访问器属性查看）
3. 当前对象上查找不到的属性，就会去其`[[Prototype]]`属性指向的原型对象中查找。

这就是我们通常说的原型继承。并且由于原型对象也是对象，所以在原型对象上没有的属性，就回去原型对象的原型对象上再去查找，以此类推，直至`Object`的原型对象`null`为止。这就是 JS 中另一个非常重要的概念，原型链。

但是原型链有一些副作用：

1. 查找不存在的属性时，会遍历整个原型链。
2. 遍历对象的属性（`for in`）时，其原型链上的每个可枚举属性都会被遍历。
3. 只能修改删除对象自身的属性。

## AMD 和 CommonJS 的异同

都是为了 JS 的模块化开发（在 ES6 出现之前）。

* CommonJS 是同步的；而 AMD（Asynchronous Module Definition）是异步的。
* CommonJS 的适合在服务器端运行；而 AMD 由于是异步的，所以在浏览器端更合适。
* 从语法上来说，AMD 更为细致；而 CommonJS 更像其他语言中的`import`。并且 Node 开发中也是 CommonJS 的写法，避免了在开发中切换语法环境。
* 现在更为流行的是将所有 JS 文件打包成一个 js 文件，所以 AMD 的这种异步加载模块的方式的作用没有那么大了。

不过现在 ES6 中已经原生支持 JS 模块化了，并且支持同步与异步加载。虽然还有浏览器和低版本 Node 不支持原生 ES6 模块，但是可以通过转译器（例如 Babel）来实现。

**参考：**

1. [https://auth0.com/blog/javascript-module-systems-showdown/](https://auth0.com/blog/javascript-module-systems-showdown/)

## 为什么`function IIFE(){ }();`会报错。如何让这个 IIFE 正确运行？

因为 JS 引擎会将这条语句分为两部分：`function IIFE(){ }`函数声明和`()`。后面的`()`用于函数执行，但由于没有指定函数名，所以报错`Uncaught SyntaxError: Unexpected token )`。

有多种方式，比如：`(function IIFE(){ })()`和`(function IIFE(){ }())`。其原理就是将函数声明转换为函数表达式，然后使用`()`调用。所以不一定用`()`包裹，只要在`function`关键字前面加点东西(一元运算符)，让 JS 引擎不将其视为函数声明就可以，比如`!`、`~`、`-`以及`+`也可以，就像这样：`!function IIFE(){ }()`。

**参考：**

1. [http://benalman.com/news/2010/11/immediately-invoked-function-expression/](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)

## `null`和`undefined`以及未声明有什么不同？如何判断这些值？

* 未声明是指那些没有使用`var`、`let`以及`const`声明过的变量。直接引用这种变量会导致 JS 报错（`console.log(notExistVariable); // Uncaught ReferenceError: notExistVariable is not defined`）。
* `undefined`是指变量经过声明，但是却没有赋初始值。可以使用`foo === undefined`以及`typeof foo === 'undefined'`判断。
* `null`需要明确对变量赋值`var foo = null;`。用来表示不存在。通常对于一个不再需要的变量，就会对其重新赋值为`null`。判断`null`可以用：`!foo && typeof foo === 'object'`。

**注意：**

在使用`typeof`运算符判断变量是否不存在时，如果变量未声明过，是不会报错的，且返回的也是`undefined`：`typeof notExistVariable === 'undefined'`。所以使用`typeof`时要确认变量是否已经声明过。

## 什么是闭包？闭包都可以用来干什么？

函数闭包是一种特殊的技术，能够让一个函数访问另一个函数的作用域。具体来说就是，函数的作用域都是独立的，但是通过闭包可以实现让函数 A 中能够使用函数 B 中的局部变量，即使函数 B 已经执行完毕。

在 JS 中，函数作为一等公民，尤为常见。比如：子函数中使用了父函数作用域的变量。

```javascript
function createCounter(delta) {
  return function(x) {
    return delta + x;
  };
}

const counter1 = createCounter(1);
const counter2 = createCounter(2);

counter1(1); // 2
counter2(1); // 3
```

函数`createCounter`执行完毕之后，其局部变量`delta`理应被销毁，但是由于`counter1`和`counter2`两个函数中引用了`delte`，所以`delta`并不会被销毁，而是会被保存在特殊的闭包作用域中，使`counter1`和`counter2`两个函数可以正常运行。

闭包最常见的使用场景就是保存函数的当前执行状态，或者说函数执行时某些变量的值，比如记录上面计数器例子的结果：

```javascript
function createCounter(delta) {
  let num = 0;
  return function() {
    num += delta;
    console.log(num);
    return num;
  };
}

const counter1 = createCounter(1);
const counter2 = createCounter(2);

counter1(); // 1
counter1(); // 2
counter1(); // 3
counter2(); // 2
counter2(); // 4
counter2(); // 6
```

初次之外，常见的场景包括：

* 解决`for`循环中变量引用的问题
* 封装对象（私有属性）
* 模块化开发
* 柯里化

**参考：**

1. [https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)

## 解释下`forEach()`和`map()`有什么不同以及各自的适用场景。

两者都会对数据的每一项执行灰调函数，但是

* `forEach()`没有返回值；
* `map()`会返回一个新的数组。（新数组每一项是遍历回调的返回值）

所以如果想根据一个数组获得一个新的数组，就使用`map`；如果只是想遍历数组，就使用`forEach`。

## 对于`function Person(){}`，`var person = Person()`和`var person = new Person()`有什么不同？

```javascript
function Person(name) {
  this.name = name;
}

var person1 = Person('foo');
var person2 = new Person('bar');
```

首先对于`Person`来说，它就是普通的函数，所以重要的是调用这个函数的方式（是否带`new`）。

* 对于不带`new`的普通函数调用，由于`Person`没有指定返回值，所以`person1`等于`undefined`；并且会在全局`window`对象上**意外**的创建一个值为`foo`的变量`name`。
* 带上`new`的调用，又成为构造函数调用，具体过程为：创建一个空对象，该对象的原型就是构造函数的原型对象；以该对象作为`this`执行构造函数；返回该对象。

## 使用Ajax的优缺点

优点：

- 交互性更好。仅需要刷新页面的局部内容就可以实现动态渲染。
- 按需加载。仅需加载初始页面所需的js和css。

缺点：
- 前进后退和书签功能需要额外的工作。
- SEO非常不友好。
