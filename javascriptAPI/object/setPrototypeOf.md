# Object.setPrototypeOf()

## 语法

```js
Object.setPrototypeOf(obj, prototype);
```

## 描述
方法设置一个指定的对象的原型 ( 即, 内部[[Prototype]]属性）到另一个对象或  null。

- `obj` 要设置其原型的对象。

!> 
`Object.getPrototypeOf()` 和 `Object.setPrototypeOf()` 存在的意义就是避免让我们写 `__proto__`，因为它严格意义上不是一个标准的属性。

### 例子

```js
let dict = Object.setPrototypeOf({}, null); // 设置一个纯净的对象
```

new 两种实现方法
```js
function Person(name) {
	this.name = name;
}

//(1)
const o = {};
o.__proto__ = Foo.prototype;
Foo.call(o, 'xm');

//(2)
const o = {};
Object.setPrototypeOf(o, Foo.prototype)
Foo.call(o, 'xm');
```

完整的new实现
```js
function create(){
  //创建一个空对象
  let obj = new Object();
  //获取构造函数
  let Constructor = [].shift.call(arguments);
  //链接到原型
  Object.setPrototypeOf(obj, Constructor.prototype)
  //绑定this值
  let result = Constructor.apply(obj,arguments);//使用apply，将构造函数中的this指向新对象，这样新对象就可以访问构造函数中的属性和方法
  //返回新对象
  return typeof result === "object" ? result : obj;//如果返回值是一个对象就返回该对象，否则返回构造函数的一个实例对象
}

function Person(name){
	this.name = name;
}
let p = create(Person, 'xm');

p.name; // xm
```