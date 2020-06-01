# isPrototypeOf()

## 语法

```ts
prototypeObj.isPrototypeOf(object):boolean
```

## 描述
用于指示对象是否存在于另一个对象的原型链中。如果存在，返回true，否则返回false。

- 所有继承了 Object 的对象都会继承到 hasOwnProperty 方法。这个方法可以用来检测一个对象是否含有特定的自身属性；和 in 运算符不同，该方法会忽略掉那些从原型链上继承到的属性。

## 示例

#### 使用 hasOwnProperty 方法判断属性是否存在
```js
let o = {};
o.p = 'p';
o.hasOwnProperty('p'); // true
o.hasOwnProperty('0'); // false
```

#### 自身属性与继承属性
```js
let o = {};
o.p = 'p';
o.hasOwnProperty('p'); // true
o.hasOwnProperty('toString'); // false
```

!> 
使用hasOwnProperty做为属性名

```
let foo = {
    hasOwnProperty: function() {
        return false;
    },
    bar: 'Here be dragons'
};
foo.hasOwnProperty('bar'); // 始终返回 false
// 如果担心这种情况，可以直接使用原型链上真正的 hasOwnProperty 方法
({}).hasOwnProperty.call(foo, 'bar'); // true

// 也可以使用 Object 原型上的 hasOwnProperty 属性
Object.prototype.hasOwnProperty.call(foo, 'bar'); // true
```