# 提升

> JavaScript代码在执行时是由上到下一行一行执行的，这种说话不完全正确。

**包括变量和函数在内的所有声明都会在任何代码被执行之前首先被处理**

如下例：

```javascript
a = 2;
var a;
console.log(a);//2

所以这里首先被执行的是'var a;'
```

```javascript
console.log(a)//undefinded

var a = 2;

var a = 2;可以看做是var a,
a = 2,两个声明
```

上述例子的现象的过程就好像变量和函数声明从它们代码中出现位置“移动”到最上面，此过程叫做提升。
**只有声明本身会被提升，赋值或者其他运行逻辑会留在原地。**

```javascript
foo()

function foo(){
    console.log(a);//undefined
    var a = 2;
}
```

```javascript
foo()//TypeError

var foo = function bar(){
    //...
}

变量标识符foo()被声明提升分配给所在的作用域，但当执行foo()时,并未赋值，所以抛出异常。
```

结论：**函数声明会被提升，函数表达式不会被提升**

函数会首先被提升，然后才是变量。

```javascript
foo(); // 1

var foo;//重复的声明，被忽略。

function foo() {
    console.log( 1 );
}
foo = function() {
    console.log( 2 );
};
```

## 小结

+ var a = 2,JavaScript引擎将其当做var a ,a = 2，两个单独的声明。

+ 无论作用域中的声明出现在什么地方，都将在代码本身被执行前首先进行处理。
