# Object.keys()

## 语法

```js
Object.keys(obj)
```

## 描述
返回一个对象自身 可枚举属性 组成的数组, 其排列与使用 for...in 循环遍历该对象时返回的顺序一致, 不同的是 Object.keys() 不会枚举 原型链上的属性. 此外, 两者都不会遍历 Symbol 属性。

- `obj` 要返回其枚举自身属性的对象。

### 例子
```js
const obj = {
    name: 'cocon',
    age: 10,
    [Symbol('symbol')]: 'symbol',
    say(){}, 
};

Object.defineProperty(obj, 'testEnumerable', {
  value: 'testEnumerable',
  enumerable: false,
});

Object.keys(obj); // ["name", "age", "say"]
```

Object.keys() 不会返回 `原型链` 上的属性, 而 for...in 可以。
```js
function Person(name) {
    this.name = name;
}
Person.prototype.say = function() {
    console.log('say~');
}
let cocon = new Person('cocon');

Object.keys(cocon); // ['cocon']

for (const i in a) {
  console.log(i); // cocon say
}
```