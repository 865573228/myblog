# Object.entries()

## 语法

```js
Object.entries(obj)
```

## 描述
可以把一个对象的键值以数组的形式遍历出来，结果和 for...in 一致，但不会遍历原型属性。

- `obj` 要返回其枚举自身属性的对象。

### 例子

对象
```js
Object.entries({
    name: 'cocon',
    age: 10,
    [Symbol('symbol')]: 'symbol',
    say(){}, 
}); 
// [["name","cocon"],["age",10],["say",null]]
```

数组
```js
Object.entries([1,2,3]); // [["0",1],["1",2],["2",3]]
```

数字
```js
Object.entries(12); // []
```

字符串
```js
Object.entries('aaa'); // [["0","a"],["1","a"],["2","a"]]
```