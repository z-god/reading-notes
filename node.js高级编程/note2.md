# Node核心API基础

## 3 加载模块

### 3.1 node如何加载模块

Node模块大致分为：自定义、npm安装、核心模块。

不管什么模块都可以使用require函数

+ 加载核心模块

```javascript
var module = require('module_name');

此代码会导入一个核心模块或者由NPM安装的模块
```

+ 加载文件模块

```javascript
例：
var module = require(./moduledir/my_module)

可以省略文件扩展名.js。如果没有找到该文件，Node会加上扩展名再次查找。
```

+ 加载文件夹模块

```javascript
var module = require(./moduledir)

Node会假定该文件夹是一个包，并试图查找该包。包定义在package.json中。
如果文件中不存在定义，报的入口点会假定为默认值index.js
```

### 3.2 导出模块

> 对于足够复杂的应用程序，应该将一些类、对象或者函数划分成定义良好的可重用的模块，模块只对外暴露指定的内容。

```javascript
function Foo(){
    //...
}

module.exports = Foo;
```

module是一个变量，表示当前模块自身。

module.exports被初始化一个空对象，可以为这个空对象附加上任意想导出的属性。

```javascript
function Foo1(){
    //..
}

module.exports.fooA = Foo1;
```

### 3.3 缓存模块

模块首次加载会被缓存起来，如果模块名能被解析成相同的文件名，那么每次调用都会确切返回同一模块。

### 3.4 小结

+ 可以使用require()函数从文件夹加载核心模块、第三方模块或者自定义模块。

+ 可以使用文件相对或者绝对路径加载非核心模块。

+ 可以编写JavaScript文件导出表示模块API的对象，来创建自定义模块。