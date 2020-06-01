# Object.defineProperty()

## 语法

```js
Object.defineProperty(obj, prop, descriptor)
```

## 描述
方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回这个对象。

该方法允许精确添加或修改对象的属性。通过赋值操作添加的普通属性是可枚举的，能够在属性枚举期间呈现出来（for...in 或 Object.keys 方法）， 这些属性的值可以被改变，也可以被删除。这个方法允许修改默认的额外选项（或配置）。默认情况下，使用 Object.defineProperty() 添加的属性值是不可修改的。

- `obj` 要在其上定义属性的对象。

- `prop` 要定义或修改的属性的名称。

- `descriptor` 将被定义或修改的属性描述符。

## 属性描述符
对象里目前存在的属性描述符有两种主要形式：数据描述符和存取描述符。数据描述符是一个具有值的属性，该值可能是可写的，也可能不是可写的。存取描述符是由getter-setter函数对描述的属性。
(定义了 value 或 writable，一定不能有 get 或 set，反之亦然，否则直接报错)

- `configurable` 当且仅当该属性的 configurable 为 true 时，该属性描述符才能够被改变，同时该属性也能从对应的对象上被删除。默认为 false。

- `enumerable` 当且仅当该属性的enumerable为true时，该属性才能够出现在对象的枚举属性中。默认为 false。

- `value` 该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。

- `writable` 当且仅当该属性的writable为true时，value才能被赋值运算符改变。默认为 false。

- `get` 一个给属性提供 getter 的方法，如果没有 getter 则为 undefined。当访问该属性时，该方法会被执行，方法执行时没有参数传入，但是会传入this对象（由于继承关系，这里的this并不一定是定义该属性的对象）。默认为 undefined。

- `set` 一个给属性提供 setter 的方法，如果没有 setter 则为 undefined。当属性值修改时，触发执行该方法。该方法将接受唯一参数，即该属性新的参数值。默认为 undefined。


|            | configurable | enumerable | value | writable | get | set |
| ---------- | ------------ | ---------- | ----- | -------- | --- | --- |
| 数据属性   | Yes          | Yes        | Yes   | Yes      | No  | No  |
| 访问器属性 | Yes          | Yes        | No    | No       | Yes | Yes |

### Configurable
```js
const obj = {};

Object.defineProperty(obj, 'name', {
	value: 'cocon',
	configurable: false
});

obj.name = 'cocon2';
// name 没有被赋值
obj.name; // cocon
// name 没有被删除
// 非严格模式下删除属性会显示false, 严格模式会报错
delete obj.name; // false
```

### Enumerable
```js
const obj = {
    name: 'cocon',
    age: 22
}

Object.defineProperty(obj, 'income', {
  value: '10,000,000',
  enumerable: false,
});

// 不能输出income的信息
for (const i in obj) {
  console.log(obj[i]);
}

obj.propertyIsEnumerable('income'); // false
```

### Writable
```js
const obj = {
    age: 22
};

Object.defineProperty(obj, 'name', {
	value: 'cocon',
    configurable: true,
    writable: true,
});

// name 可修改
// 当configurable定义为false时, name也可以被修改
// 只要writable为true,就可以任意定义
obj.name = 'cocon2';
obj.name; // cocon2
```

### Getter & Setter
```js
const obj = {};

Object.defineProperty(obj, 'name', {
    configurable: true,
    get: function() {
        console.log(`获取数据`);
    },
    set: function(val) {
        console.log(`设置了${val}`);
    }
});

obj.name = 'cocon'; // 设置了cocon
obj.name; // 获取数据
```