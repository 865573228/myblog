# call()

## 语法

```js
fun.call(thisArg, arg1, arg2, ...)
```

## 描述
方法使用一个指定的 this 值和单独给出的一个或多个参数来调用一个函数。

- 不传，或者传null，undefined， this指向window对象

- 传递另一个函数的函数名fun2，this指向函数fun2的引用

- 值为原始值(数字，字符串，布尔值),this会指向该原始值的自动包装对象，如 String、Number、Boolean

- 传递一个对象，函数中的this指向这个对象

!>
注意: this 永远指向最后调用它的那个对象。

!>
注意：该方法的语法和作用与 `apply()` 方法类似，只有一个区别，就是 `call()` 方法接受的是一个参数列表，而 `apply()` 方法接受的是一个包含多个参数的数组。

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
foo.getName.call(obj); // cocon2
```

#### 模拟实现call
```js
// 简单版本
Function.prototype.call2 = function(content, ...args) {
    content.fn = this;
    const result = content.fn(...args);
    delete content.fn;
    return result;
}

// 完整版
Function.prototype.call2 = function(content, ...args) {
    const fn = Symbol('fn');
    if (!content || content === null || content === undefined) {
        content = window;
    }
    const con = Object(content);
    con.fn = this;
    const result = con.fn(...args);
    delete con.fn;
    return result;
}

```

