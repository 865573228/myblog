# Object.freeze()

## 语法

```js
Object.freeze(obj)
```

## 描述
Object.freeze() 方法可以冻结一个对象。

- 冻结指的是不能向这个对象添加新的属性，不能修改其已有属性的值，不能删除已有属性，以及不能修改该对象已有属性的可枚举性、可配置性、可写性。也就是说，这个对象永远是不可变的。该方法返回被冻结的对象。

- 此对象的 原型 也不能被修改

- `obj` obj 将要被冻结的对象。

- 但是，当某个属性的属性值是 对象 时，该属性可以被修改，除非它也是个冻结对象

### 例子

```js
let obj = {
	name: 'cocon',
	age: 22
}
Object.freeze(obj);

// 不可以修改成功
obj.name = 'cocon2';

// 不可以添加新的属性,严格模式会抛出TypeError
obj.say = 'say';

// 不可以删除已经有的属性,严格模式会抛出TypeError
delete obj.name;

function Person(name) {
	this.name = name;
}
Person.prototype.say = function(){ 
	return this.name
}

let p = new Person('cocon');

Object.freeze(p);

p.name; // cocon

// 修改不生效
p.name = 'cocon2';

delete p.name; // false

```