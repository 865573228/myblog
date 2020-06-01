# Object.fromEntries()

## 语法

```js
Object.fromEntries(iterable);
```

## 描述
Object.fromEntries() 方法是 Object.entries() 的逆操作，用于将一个键值对数组转为对象。

- `obj` 要返回其枚举自身属性的对象。

### 例子
```js
const obj = Object.fromEntries([['foo', 'bar'], ['baz', 42]]);
// {foo: "bar", baz: 42}
```