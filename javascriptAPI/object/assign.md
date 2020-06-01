# Object.assign()

## 语法

```js
Object.assign({}, {});
```

## 描述
方法用来将源对象（source）的所有可枚举属性，复制到目标对象（target）。它至少需要两个对象作为参数，第一个参数是目标对象，后面的参数都是源对象。

- 仅有一个值的时候，只会返回这一个值。

- 目标对象里的属性会被源对象覆盖，后面的会覆盖前面的。

- 当源参数是基本数据类型时，null 和 undefined 会被忽略。源参数为对象时， null undefined number boolean sysmbol 将会被忽略。

- 如果源对象中有值是对象，那么得到的结果为对象的引用(浅拷贝)。

## 示例

```js
let a = {a: 1}, b = {b: 2}, c = null, d = {d: {dd: 11}};

// 合并对象
Object.assign(a, b); // {a: 1, b: 2}

// null被忽略
Object.assign(a, c); // {a: 1}

// null undefined number boolean sysmbol 被忽略
Object.assign({}, 0, 'a', Symbol('name'), null, undefined, true); // { '0': 'a' }

// 源对象中有值是对象，那么得到的结果为对象的引用
let s = Object.assign({}, d);
d.d.dd = 222;
e.d === d.d; // true

```

### 用途

#### 为对象添加属性
```js
class Point {
	constructor(x, y) {
		Object.assign(this, {x, y});
	}
}
let p = new Point(1,2); 
p.x = 1;
p.y = 2;
```

#### 为对象添加方法（方法一等同方法二）
```js
function Point() {}
// 方法一
Point.prototype.say = function () { 
    console.log('hello');
}
// 方法二
Object.assign(Point.prototype, {
    say(){
        console.log('hello');
    }
})
let p = new Point();
p.say(); // hello
```