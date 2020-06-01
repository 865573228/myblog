# Object.seal()

## 语法

```js
Object.seal(obj)
```

## 描述
方法可以让一个对象密封，并返回被密封后的对象。密封对象是指那些不能添加新的属性，不能删除已有属性，以及不能修改已有属性的可枚举性、可配置性、可写性，但可以修改已有属性的值的对象。

- `obj` obj 将要被密封的对象。

### 例子

```js
let obj = {
	name: 'cocon',
	age: 22
}
Object.seal(obj);

// 可以修改成功
obj.name = 'cocon2';

// 不可以添加新的属性,,严格模式会抛出TypeError
obj.say = 'say';

// 不可以删除已经有的属性,严格模式会抛出TypeError
delete obj.name;
```