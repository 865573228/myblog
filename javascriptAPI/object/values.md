# Object.values()

## 语法

```js
Object.values(obj)
```

## 描述
返回一个对象自身 `可枚举属性的属性值` 组成的数组, 其排列与使用 for...in 循环遍历该对象时返回的顺序一致, 不同的是 `Object.values()` 不会枚举 `原型链上的属性`. 此外, 两者都不会遍历 `Symbol` 属性.

- `obj` 要返回其枚举自身属性的对象。

### 例子

对象
```js
Object.values({
    name: 'cocon',
    age: 10,
    [Symbol('symbol')]: 'symbol',
    say(){}, 
}); 
// ['cocon', 10, f()]
```