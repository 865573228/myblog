# Object.preventExtensions()

## 语法

```js
Object.preventExtensions(obj)
```

## 描述
方法让一个对象变的不可扩展，也就是永远不能再添加新的属性。

- `obj` 将要变得不可扩展的对象。

### 例子

```js
let obj = {
    name: 'cocon',
    age: 22
}
Object.preventExtensions(obj);

obj.cocon = 'cocon';
obj.cocon; // undefined

delete obj.name; // 可以删除

obj.age = 23;
obj.age; // 23 // 可以修改
```