# Object.create()

## 语法

```js
Object.create(proto, [propertiesObject])
```

## 描述
用于创建一个新的对象，它使用现有对象作为新对象的 __proto__.

- proto, 新创建对象的原型对象。

- propertiesObject(可选), 这些属性对应Object.defineProperties()的第二个参数。

## 示例

```js
const cat = {
	name: '',
	age: '',
	say() {
		console.log(`i im ${this.name}`)
	}
}

// {name: 'demo'}
const a = Object.create(cat, {
    name: {
        value: 'demo',
        writable: false,
        enumerable: true,
        configurable: false,
    }
}); 

Object.getOwnPropertyDescriptors(a);
// 输出如下
{"name":{"value":"demo","writable":false,"enumerable":true,"configurable":false}}

```

### 用途

#### 类的继承

```js

function Person(name) {
    this.name = name;
}

Person.prototype.say = function (){
    return `i'm ${this.name}`;
}

/* 传统方法 */

// 继承属性
function Stu(name) {
    Person.call(this, name);
}

// 继承方法
Stu.prototype = new Person();

let xm = new Stu('xm');

xm.name; // xm
xm.say(); // i'm xm

/* create方法 */
Stu.prototype = Object.create(Person.prototype)；
Stu.prototype.constructor = Stu;

xm.name; // xm
xm.say(); // i'm xm

```

#### Object.create() 和 new的区别

`new` 的实现
1. 新建了一个对象。
2. 设置该对象的原型(__proto__)为构造函数的原型(prototype)
3. 将new运算符后面的构造函数的作用域指向这个新对象。(将构造函数的this指向新对象)
4. 执行new后面的构造函数
5. 返回新对象

`Object.create()`的实现
```js
if (typeof Object.create !== 'function') {
  Object.create = function(proto, propertiesObject) {
    if (typeof proto !== 'object' && typeof proto !== 'function') {
      throw new TypeError('Object prototype may only be an Object: ' + proto);
    } else if (proto === null) {
      throw new Error(
        "This browser's implementation of Object.create is a shim and doesn't support 'null' as the first argument.",
      );
    }

    if (typeof propertiesObject != 'undefined')
      throw new Error(
        "This browser's implementation of Object.create is a shim and doesn't support a second argument.",
      );
    //实现一个隐藏函数
    function F() {}
    //函数的原型设置为参数传进来的原型
    F.prototype = proto;
    // 返回一个F函数的实例，即此实例的__proto__指向为参数proto
    return new F();
  };
}
```

#### Object.create(null)

因为 null 是原型链的终点，因此以 null 为 __proto__ 创建的空对象是一个完全纯净的对象



