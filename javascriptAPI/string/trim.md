# trim(), trimLeft(), trimRight()

## 语法

```ts
trim(): string;
trimLeft(): string;
trimRight(): string;
```

## 描述

- trim()用于删除字符串两侧的空格

- trimLeft()用于删除字符串左侧的空格

- trimRight()用于删除字符串右侧的空格

## 示例

```js
let str=" Visit Runoob "; 
str.trim(); // 'Visit Runoob' 
str.trimLeft(); // 'Visit Runoob '
str.trimRight(); // ' Visit Runoob'
```