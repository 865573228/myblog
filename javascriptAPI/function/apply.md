# apply()

## 语法

```js
func.apply(thisArg, [argsArray])
```

## 描述
该方法是 call 的语法糖，它的第一个参数和 call 方法相同，但第二个参数接收一个数组或者类数组，而 call 从第二个参数起接收一个参数序列。

- `thisArg`可选的。在 func 函数运行时使用的 this 值。请注意，this可能不是该方法看到的实际值：如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动替换为指向全局对象，原始值会被包装。

- `argsArray`可选的。一个数组或者类数组对象，其中的数组元素将作为单独的参数传给 `func` 函数。如果该参数的值为 `null` 或  `undefined`，则表示不需要传入任何参数。从ECMAScript 5 开始可以使用类数组对象。 浏览器兼容性 请参阅本文底部内容。

!>
注意：该方法的语法和作用与 `call()` 方法类似，只有一个区别，就是 `call()` 方法接受的是一个参数列表，而 `apply()` 方法接受的是一个包含多个参数的数组。

### 例子

```js
let obj = {
    name: 'cocon2'
}

let foo = {
    name: 'cocon',
    getName: function(...name) {
        console.log(...name)
        console.log(this.name) // cocon
    }
}

foo.getName(); // cocon
foo.getName.apply(obj); // cocon2
```

#### 模拟实现apply
```js
// 简单版本
Function.prototype.apply = function(content) {
    content.fn = this;
    const result = content.fn(...arguments[1]);
    delete content.fn;
    return result;
}

// 完整版
Function.prototype.apply = function(content) {
    const fn = Symbol('fn');
    if (!content || content === null || content === undefined) {
        content = window;
    }
    const con = Object(content);
    con.fn = this;
    const result = arguments[1] ? con.fn(...arguments[1]) : con.fn();
    delete con.fn;
    return result;
}
```

