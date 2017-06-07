### 原型对象

  原型对象可以看作是对象的基类，几乎所有的函数都有一个prototype属性，该属性是   
一个原型对象 用来创建 新的对象实例。所有创建的 对象实例 共享该 原型对象，并且
这些 对象实例 可以访问 原型对象 的属性
```js 
  var book = {
    title:"javascript"
  }
  console.log('title' in book)  //true
  console.log(book.hasOwnProperty('title')) //true
  console.log('hasOwnProperty' in book) //true
  console.log(book.hasOwnProperty('hasOwnProperty')) //false
  console.log(Object.prototype.hasOwnProperty('hasOwnProperty'))//true
```
  * in操作符对原型属性和自有属性都返回true

### 鉴别原型属性

```js 
  function hasPrototypeProperty(object,name){
    return name in object && !object.hasWOwnProperty(name);
  }
```

### [[Ptototype]]

  一个对象实例通过内部属性`[[Prototype]]`跟踪其原型对象，该属性是一个指向该实例使用的原型对象的指针  
  用new创建一个新的对象时，构造函数的原型对象 就会被赋值给 该对象的`[[Prototype]]`属性

### 读取`[[Ptototype]]`

  1. Object.getPrototypeOf()
```js 
  var object = {};
  var prototype = Object.getPrototypeOf(object);
  console.log(prototype === Object.prototype)//true
```
  2. __proto__
  __proto__可以直接读写`[[Prototype]]`属性

### 检测原型对象

  isPrototypeOf()方法可以用来检测某个对象是否是另一个对象的 原型对象
```js 
  var object = {};
  console.log(Object.prototype.isPrototypeOf(object)) //true
```

### 原型链

  当读取一个对象的属性时，JavaScript引擎首先在该对象的自有属性中查找属性名字，如果找到则返回。如果自有属性
中不包含该名字，这JavaScript会搜索`[[Prototype]]`中的对象，找到返回找不到则继续向上查找，找到顶层  
（Object.prototype.__proto__==>null）还是没有则返回undefined，这个查找的过程形成的链路就称之为原型链