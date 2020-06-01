# charCodeAt()

## 语法

```ts
charCodeAt(str: number | string): string;
```

## 描述

可返回指定位置的字符的 Unicode 编码

- 传入函数值不区分 `1 | '1'`

- 当 传入 `''` 或 不传值, 返回第一个字符的 Unicode 编码

- 当参数 `< 0 || > str.length - 1`, 返回 `NaN`

## 示例

```js
let str = 'abc例子defg😆';
str.charCodeAt(1); // 98
str.charCodeAt('1'); // 98
str.charCodeAt(); // 97
str.charCodeAt(333); // NaN
```