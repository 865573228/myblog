# Object.getPrototypeOf()

## 语法

```js
Object.getPrototypeOf(obj);
```

## 描述
方法返回指定对象的原型（内部[[Prototype]]属性的

- `obj` 要返回其原型的对象。

!> `__proto__` 并不是语言本身的特性，这是各大厂商具体实现时添加的私有属性，虽然目前很多现代浏览器的 JS 引擎中都提供了这个私有属性，但依旧不建议在生产中使用该属性，避免对环境产生依赖。生产环境中，我们可以使用 `Object.getPrototypeOf` 方法来获取实例对象的原型，然后再来为原型添加方法/属性。

### 例子

```js
let obj = {
	name: 'cocon'
};

Object.getPrototypeOf(obj) === obj.__proto__ // true
```

```js
function Person() {
	return 'hellp';
}

let p = new Person();

Person.prototype === Object.getPrototypeOf(p); // true
```

```js
let proto = {};
let obj = Object.create(proto);
Object.getPrototypeOf(obj) === proto; // true
```