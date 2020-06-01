# match()

## 语法

```js
match(regexp);
```

## 描述

 match() 方法检索返回一个字符串匹配正则表达式的的结果。


- `regexp`为正则表达式，如果传入的不是正则表达式则会使用`new RegExp(regexp)`转为正则表达式

- `//ig` i会匹配大小写，g会匹配全局

## 示例

```js
let str = 'testmatchT';
str.match('s'); // ["s", index: 2, input: "testmatch", groups: undefined]
str.match(/s/); // ["s", index: 2, input: "testmatch", groups: undefined]
str.match(/t/g); // ["t", "t", "t"]
str.match(/t/ig); // ["t", "t", "t", '"T"]
str.match(null); // null
```