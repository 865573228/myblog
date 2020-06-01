# Object.getOwnPropertyDescriptors()

## 语法

```js
Object.getOwnPropertyDescriptors(obj);
```

## 描述

用来获取一个对象所有自有属性的描述符，如果没有任何自身属性，则返回空对象。

-   `obj` 需要查找的目标对象。

### 例子

```js

let obj = {
    name: 'cocon'
};

Object.defineProperties(obj, {
  age: {
    value: 22,
    enumerable: false,
  },
  lastName: {
    get() {
      return 'hello';
    },
  },
});

obj.__proto__ = {
    'copy': 'copy'
}

Object.getOwnPropertyDescriptors(obj);
// 结果如下, 可以看到是defineProperty的第二个参数
{
    "name": {
        "value": "cocon",
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "age": {
        "value": 22,
        "writable": false,
        "enumerable": false,
        "configurable": false
    },
    "lastName": {
        "enumerable": false,
        "configurable": false
    }
}
```

#### 解决 Object.assign() 浅拷贝问题
```js
let obj = {
    name: 'cocon',
	say(){
		return 'llllll'
	}
};

Object.defineProperties(obj, {
  age: {
    value: 22,
    enumerable: false,
  },
  lastName: {
    get() {
      return 'hello';
    },
  },
});

obj.__proto__ = {
    'copy': 'copy'
}

let objCopy = Object.assign({}, obj);

Object.getOwnPropertyDescriptors(obj)
// 输出结果
{
    "name": {
        "value": "cocon",
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "say": {
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "age": {
        "value": 22,
        "writable": false,
        "enumerable": false,
        "configurable": false
    },
    "lastName": {
        "enumerable": false,
        "configurable": false
    }
}

// 只能拷贝源对象的可枚举的自身属性, 无法拷贝源对象的原型
Object.getOwnPropertyDescriptors(objCopy)
// 输出结果
{
    "name": {
        "value": "cocon",
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "say": {
        "writable": true,
        "enumerable": true,
        "configurable": true
    }
}

// 可以通过以下方式来深拷贝对象
const copyObj = Object.create(
  Object.getPrototypeOf(obj),
  Object.getOwnPropertyDescriptors(obj),
);

Object.getOwnPropertyDescriptors(copyObj);
// 输出结果
{
    "name": {
        "value": "cocon",
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "say": {
        "writable": true,
        "enumerable": true,
        "configurable": true
    },
    "age": {
        "value": 22,
        "writable": false,
        "enumerable": false,
        "configurable": false
    },
    "lastName": {
        "enumerable": false,
        "configurable": false
    }
}
```