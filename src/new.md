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
  (对象字面量或者Object构造函数创建出来的对象，其构造属性指向Object)
```js 
  function Person(){
    //...
  }
  var person1 = new Person();
  console.log(person1.constructor === Person) // true
```

### 构造函数的检测

  1. constructor（构造函数属性容易被覆盖，不完全准确）  
  2. instanceof（推荐使用）
```js 
  function Person(){
    //...
  }
  var person1 = new Person();
  console.log(person1 instanceof Person) //true
```

### 目的

  使用构造函数的目的是为了轻松创建许多拥有相同属性和方法的对象
```js 
  function Person(name){
    this.name = name;
    this.sayName = function(){
      console.log(this.name)
    }
  }
  var person1 = new Person('张三');
  var person2 = new Person('李四');

  console.log(person1.name); //张三
  console.log(person2.name); //李四

  person1.sayName(); //张三
  person2.sayName(); //李四
```
  * 注意：在构造函数中显式调用return 如果返回值是一个对象，它会代替新创建的
  对象实例返回；如果返回值是一个原始类型，这个原始类型返回值会被忽略，新创建的
  对象实例会被返回