# lastIndexOf()

## 语法

```ts
lastIndexOf(str: string, num?: number): number;
```

## 描述

方法返回指定值在调用该方法的字符串中最后出现的位置，如果没找到则返回 -1。从该字符串的后面向前查找，从 fromIndex 处开始。

- `str`表示要搜索的字符串

- `num`表示从哪个位置开始搜索，默认为`str.length`，小于`0`默认为`0`,大于`str.length`默认为`str.length`

- 匹配不上返回`-1`

## 示例

```js
let str = 'ftestlastIndexOf';
str.lastIndexOf('f'); // 15
str.indexOf('test', 2); // -1
str.indexOf('x', 2); // -1
```