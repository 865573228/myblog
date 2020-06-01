# charAt()

## 语法

```ts
charAt(str: number | string): string;
```

## 描述

可返回指定位置的字符

- 传入函数值不区分 `1 | '1'`

- 当 传入 `''` 或 不传值, 返回第一个字符

- 当参数 `< 0 || > str.length - 1`, 返回 `''`

!>
charAt() 不能正确处理4字节字符

## 示例

```js
let str = 'abc例子defg😆';
str.charAt(1); // b
str.charAt('1'); // b
str.charAt('测试'); // ''
str.charAt(333); // ''
str.charAt(9); // �
```