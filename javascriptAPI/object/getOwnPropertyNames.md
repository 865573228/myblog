# Object.getOwnPropertyNames()

## 语法

```js
Object.getOwnPropertyNames(obj: any): string[];
```

## 描述
方法返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括Symbol值作为名称的属性）组成的数组。

- `obj` 一个对象，其自身的可枚举和不可枚举属性的名称被返回

- 当不存在普通字符串作为名称的属性时返回一个空数组

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

Object.getOwnPropertyNames(obj); // ["name", "say", "add"]

```

方法同样适用于数组，会返回数组的length属性
```js
Object.getOwnPropertyNames(['a', 'b', 'c'])
```
