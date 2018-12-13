# 4 应用缓冲区处理、编码和解码二进制数据

> JavaScript善于处理字符串，不善于处理二进制数据。

Node引入一个二进制缓冲区实现，该实现以Buffer伪类中的JavaScriptAPI形式暴露给外界。

*Buffer*类占用的内存会占据一个不会被修改的永久内存地址。

## 创建缓冲区

```javascript
var buf1 = new Buffer('hello newman!');

var buf2 = new Buffer('8b76fde713ce','base64')
```

可接受的编码格式：

+ ASCII

+ UTF-8

+ Base64

没有具体内容初始化，也可通过指定容量大小来创建缓冲区。

```javascript
var buf3 = new Buffer(1024);
```

## 在缓冲区获取和设置数据

使用[]操作符访问缓冲区某个字段。**当被创建一个已被初始化的缓冲区时，缓冲区中包含的是一些随机值**

## 切分缓冲区

```javascript
var buf = new Buffer("hello newman")

var newbuf = buf.slice(5)
console.log(newbuf.toString());//->"newman"
```

切分缓冲区并没用分配新的内存，也没有复制，新缓冲区使用的是父缓冲区的内存区域。

## 复制缓冲区

使用copy方法。

```javascript
var bufA = new Buffer('this is my reading note ！')
var bufB = new Buffer(12)

var bufAStart = 0;
var bufBStart = 11;
var bufBEnd = 23;

bufA.copy(bufB,bufAStart,bufBStart,bufBEnd);

console.log(bufB.toString())//->"reading notes"
```

## 缓冲区解码

```javascript
var str = buf.toString()
```