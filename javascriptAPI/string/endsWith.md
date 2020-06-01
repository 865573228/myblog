# endsWith()

## 语法

```ts
endsWith(str: string, num?: number): boolean;
```

## 描述

endsWith()方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。

- 传入`''`返回`true`

- 传入`str`为`''`, `num`为任意值结果都为`true`

## 示例

```js
let str = 'abcd';
str.endsWith('d'); // true
str.endsWith('cd'); // true
str.endsWith('a'); // false
str.endsWith('c', 3); // true
str.endsWith(''); // true
str.endsWith('', 99); // true
```