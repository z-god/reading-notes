# 使用事件发射器简化事件绑定

## 标准回调模式

> 异步编程并不使用函数返回值表示函数调用结束，而是采用后即传递风格取而代之。

```javascript
var fs = require('fs')

fs.readFile('README.md',function(err,fileContent){
    if(err){
        throw err;
    }
    console.log('file content',fileContent.toString());
})
```

后继传递风格中，每个函数在执行完毕后都会调用一个回调函数，以使程序能够继续运行下去。

## 事件发射器模式

> 使用事件发射器时，会涉及两个或者多个对象，包括发射事件的对象（事件发射器）以及一个或多个绑定到事件发射器上的代码（事件监听器）。

```javascript
var req = http.request(options,function(response){
    response.on("data",function(data){
        console.log("hi newman",data);
    })
    response.on("end",function(){
        console.log("response ended");
    })
})

req.end();
```

## 事件类型

发射的事件具有类型，类型用一个字符串表示，都是由事件发射器定义的任意字符串，事件类型通常是由不包含空格的小写单词组成的。

Node中的大多数事件发射器实现在程序发生错误时都会发着“error”事件。

## 事件发射器API

+ .addLinstener() & on()为指定类型的事件添加事件监听器。

+ .once()为指定类型的事件绑定一个仅会被调用一次的事件监听器。

+ removeEventListener()删除绑定到指定事件上的某个指定事件监听器。

+ removeAllEventListener()删除绑定到指定事件上的所有监听器。

## 小结

+ 事件发射器模式是Node中一种可重入模式，可以用它将时间发射器对象与关注一组特定事件的代码解耦。
