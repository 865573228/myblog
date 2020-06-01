# repeat()

## 语法

```ts
repeat(count: number): string;
```

## 描述

 构造并返回一个新字符串，根据`count`值决定从新重复多少次。

- `count`介于0和正无穷大之间的整数 : [0, +∞) 。表示在新构造的字符串中重复了多少遍原字符串。

- `count`为小数则会自动舍去小数点转为整数

## 示例

```js
'abc'.repeat(); // ''
'abc'.repeat(2); // 'abcabc'
'abc'.repeat(1/0); // Uncaught RangeError: Invalid count value
"abc".repeat(3.5)    // "abcabcabc"
```