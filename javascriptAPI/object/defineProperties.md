# Object.defineProperties()

## 语法

```js
Object.defineProperties(obj, prop, descriptor)
```

## 描述
跟 `defineProperty` 一样，只不过可以定义多个属性。


### 例子
```js
const obj = {};

Object.defineProperty(obj, {
	name: {
        value: 'name',
	    configurable: false
    },
    age: {
        value: 'age',
	    configurable: true
    },
});
```