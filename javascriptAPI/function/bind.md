# bind()

## 语法

```js
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

## 描述
bind() 方法会创建一个新的函数，称为绑定函数。与 call() 和 apply() 不同的是，bind() 方法不会立即执行调用它的函数，而是返回对绑定函数的引用。在调用这个绑定函数时，thisArg 就会作为函数的 this。

- `thisArg`调用绑定函数时作为this参数传递给目标函数的值。 如果使用`new`运算符构造绑定函数，则忽略该值。当使用`bind`在`setTimeout`中创建一个函数（作为回调提供）时，作为`thisArg`传递的任何原始值都将转换为`object`。如果`bind`函数的参数列表为空，执行作用域的`this`将被视为新函数的`thisArg`。

- `arg1, arg2`当目标函数被调用时，预先添加到绑定函数的参数列表中的参数。


### 例子

```js
let obj = {
    name: 'cocon2'
}

let foo = {
    name: 'cocon',
    getName: function() {
        console.log(this.name) // cocon
    }
}

const fn = foo.getName;
fn();// undefined

const fn = foo.getName.bind(foo);
fn();// cocon
```

#### 模拟实现bind
```js
// 简单版本
Function.prototype.bind2 = function (context) {
    return () => {
        return this.call(context);
    }
}

// 完整版
Function.prototype.call2 = function(thisArg, ...args) {
    if (typeof this != 'function') {
        throw TypeError('not a function');
    }
    const fn = this;

    const resFn = function() {
        // this instanceof resFn === true 时,说明返回的 resFn 被当做 new 的构造函数调用
        return fn.call(this instanceof resFn ? this : thisArg, ...args);
    };

    function F() {}
    F.prototype = this.prototype;
    resFn.prototype = new F();

    return resFn;
}
```

