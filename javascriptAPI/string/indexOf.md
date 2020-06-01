# indexOf()

## 语法

```ts
indexOf(str: string, num?: number): number;
```

## 描述

方法返回调用  String 对象中第一次出现的指定值的索引，开始在 fromIndex 进行搜索。

- `str`表示要搜索的字符串

- `num`表示从哪个位置开始搜索，默认为`0`，小于`0`也默认为`0`

- 匹配不上返回`-1`

## 示例

```js
let str = 'testindexOf';
str.indexOf('t'); // 0
str.indexOf('test'); // 0
str.indexOf('test', 2); // -1
```