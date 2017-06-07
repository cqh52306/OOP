### 什么是构造函数

  构造函数就是用new操作符创建对象时调用的函数，构造函数也是函数，同普通函数的最大区别就是  
  构造函数首字母大写（俗家约定）    
  构造函数的好处就是同一构造函数创建的对象具有相同的属性和方法 
```js 
  function Person(){
    //...
  }
```

### 构造函数实例化

  构造函数不会显式的返回任何东西，一切都是new操作符自动创建给定类型的对象自动返回  
```js 
  function Person(){
    //...
  }
  var person1 = new Person();
  var person2 = new Person; //不传参时可以忽略小括号
```

### 构造函数属性-constructor

  constructor 每个对象在创建时都自动拥有一个构造函数属性，指向创建它的构造函数  
```js 
  function Person(){
    //...
  }
  var person1 = new Person();
  console.log(person1.constructor === Person) // true
```