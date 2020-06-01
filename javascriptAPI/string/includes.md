# includes()

## 语法

```ts
includes(str: string, num?: number): boolean;
```

## 描述

方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false。

- `str`表示要搜索的字符串

- `num`表示从哪个位置开始搜索，默认为`0`，小于`0`也默认为`0`

- 什么都不传入，返回false

## 示例

```js
let str = 'testincludes';
str.includes('tes'); // true
str.includes('tes', 0); // true
str.includes('tes', 1); // false
str.includes(); // false
```