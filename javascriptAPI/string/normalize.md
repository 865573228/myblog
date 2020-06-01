# normalize()

## 语法

```js
normalize(form);
```

## 描述

 方法会按照指定的一种 Unicode 正规形式将当前字符串正规化.
 `form` 可选择的值有四种 

- NFC：Unicode 规范化格式 C
- NFD：Unicode 规范化格式 D
- NFKC：Unicode 规范化格式 KC
- NFKD：Unicode 规范化格式 KD

## 示例

```js
let str = '\u1E9B\u0323';

str.normalize('NFC'); // '\u1E9B\u0323'
str.normalize('NFD'); // '\u017F\u0323\u0307'
```