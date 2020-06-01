# Object.isSealed()

## 语法

```js
Object.isSealed(obj): boolean;
```

## 描述
用于判断一个对象是否被密封。 对于一个 不可扩展 的对象，如果它是一个 空对象 ，那么它是 被密封 的；但如果它是个 非空对象 ，并且里面的属性是 可配置的，那么该对象 不是被密封 的，因为密封对象的所有自身属性必须是不可配置的。

- `obj` obj 将要被密封的对象。

### 例子

```js
let obj = {};

Object.isSealed(obj);

// 如果把一个空对象变得不可扩展,则它同时也会变成个密封对象.
Object.preventExtensions(obj);
Object.isSealed(obj); // true

// 但如果这个对象不是空对象,则它不会变成密封对象,因为密封对象的所有自身属性必须是不可配置的.
let obj = {
	name: 'cocon'
};
Object.preventExtensions(obj);
Object.isSealed(obj); // false

//如果把这个属性变得不可配置,则这个对象也就成了密封对象.
Object.defineProperty(obj, 'name', {configurable : false});
Object.isSealed(obj);//true

```