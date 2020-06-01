# Object.getOwnPropertySymbols()

## 语法

```js
Object.getOwnPropertySymbols(obj: any): symbol[];
```

## 描述
方法返回一个给定对象自身的所有 Symbol 属性的数。

- `obj` 要返回 Symbol 属性的对象。

### 例子

```js
let obj = {
	name: 'cocon',
	[Symbol('age')]: 22,
	say() {
		return 'hello';
	}
};

Object.defineProperty(obj, 'add', {
	value: 'add',
  	enumerable: false,
})

Object.getOwnPropertySymbols(obj); // [Symbol(age)]

```
