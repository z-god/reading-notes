# this

> 一个很特别的关键字，被自动定义在左右函数作用域中。

## 为什么使用this

this提供一种更优雅的方式来隐式“传递”一个对象的引用。因此可以将API设计的更加简洁且易复用。

```javascript
function callme(){
    return this.name.toUpperCase();
}
function sayhi(){
    var greeting = "Hello,I am"+callme.call(this);
    console.log(greeting)
}

var me = {
    name: "newman"
}

callme.call(me);
sayhi.call(me);
```

## this到底是什么

> this在任何情况下都不指向函数的词法作用域。

this是在运行时绑定的，并不是在编写时绑定的，它的上下文取决于函数调用时的各种条件。this的绑定和函数声明的位置没有任何关系，只取决于函数的调用方式。

当一个函数被调用时，会创建一个活动记录，这个记录会包含函数在哪里被调用、函数的调用方法、传入的参数等信息。this就是该记录中的一个属性，会在函数执行的过程中用到。

## 小结

+ this既不指向函数自身也不指向函数的词法作用域。

+ this实际上是在函数被调用时发生的绑定，它指向什么完全取决于函数在哪里调用。