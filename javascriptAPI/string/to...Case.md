# to...Case()

## 语法

```ts
toLowerCase(): string;

toUpperCase(): string;

toLocaleLowerCase(): string;

toLocaleUpperCase(): string;
```

## 描述

 用于将指定字符串（根据本地化）全部大写（小写）。

## 示例

```js
let str="Visit Runoob!"; 
str.toLowerCase(); // visit runoob!
str.toUpperCase(); // VISIT RUNOOB
str.toLocaleLowerCase(); // visit runoob!
str.toLocaleUpperCase(); // VISIT RUNOOB!
```