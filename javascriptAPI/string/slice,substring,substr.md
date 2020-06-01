# slice(), substring(), substr()

## 语法

```ts
slice(start?: number, end?: number): string;
substring(start?: number, end?: number): string;
substr(start?: number, end?: number): string;
```

## 描述

 slice，substring,substr 三个方法都是截取字符串，但是对参数的处理有区别。
 slice，substring类似,从start截取到end位置的字符。

- slice，substring的区别在于，slice中的start如果为负数，会从尾部算起，-1表示倒数第一格，-2表示倒数第二个，end必须也为负数并且大于start。否则返回空字符串。

- slice的end如果为负数，同样从尾部算起，如果其绝对值超过原字符串长度或者为0，返回空字符串

- substring会取start和end中较小的值为start,二者相等返回空字符串，任何一个参数为负数被替换为0

- substr的end参数表示，要截取的长度,若该参数为负数或0，都将返回空字符串


!>
substr官方已经不建议使用

## 示例

```js
let str="Visit Runoob!"; 
str.slice(0,3); // Vis
str.slice(15); // ''
str.slice(-5); // noob!
```