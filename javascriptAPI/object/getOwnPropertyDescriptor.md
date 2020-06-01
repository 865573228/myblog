# Object.getOwnPropertyDescriptor()

## 语法

```js
Object.getOwnPropertyDescriptor(obj, prop)
```

## 描述
方法返回指定对象上一个自有属性对应的属性描述符。（自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性）。

- `obj` 需要查找的目标对象。

- `prop` 目标对象内属性名称。

### 例子

```js

let obj = {};

Object.defineProperty(obj, 'name', {
    value: 'cocon',
	configurable: false
});

Object.getOwnPropertyDescriptor(obj, 'name');
// {"value":"cocon","writable":false,"enumerable":false,"configurable":false}

function Person(name){
    this.name = name;
}

Person.prototype.say = function() {
    return this.name;
}

let p = new Person('cocon');

Object.getOwnPropertyDescriptor(Person, 'name')
// {"value":"Person","writable":false,"enumerable":false,"configurable":true}

// 原型链上面的属性返回undefined
Object.getOwnPropertyDescriptor(Person, 'say');
// undefined
```