# matchAll()

## 语法

```js
matchAll(regexp);
```

## 描述

 match() 方法返回与正则表达式匹配的所有结果的迭代器，包括捕获组。


- `regexp`为正则表达式，如果传入的不是正则表达式则会使用`new RegExp(regexp)`转为正则表达式

## 示例

```js
let str = 'testtestmatch';
[...str.matchAll(/test/g)]; // [["test", index: 0, input: "testtesttestmatch", groups: undefined], ["test", index: 4, input: "testtesttestmatch", groups: undefined]]
for (const match of [...str.matchAll(/test/g)]) {
  console.log(match);
}
// ["test", index: 0, input: "testtesttestmatch", groups: undefined], ["test", index: 4, input: "testtesttestmatch", groups: undefined]
```