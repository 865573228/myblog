# concat()

## 语法

```ts
concat(...string: string[]): string;
```

## 描述

用于将一个或多个字符串与原字符串连接合并，并返回一个新的字符串。

- 不传参数返回原字符串

- 参数如果是数组会被转成字符串，最后再相加

## 示例

```js
let a = 'a', b = 'b', c = 'c';
a.concat(b, c); // abc
a.concat(); // a
a.concat(b, 123); // ab123
```