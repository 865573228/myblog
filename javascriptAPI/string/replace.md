# replace()

### 语法

```ts
replace(regexp: RegExp | substr: string, newSubStr: string | function: Function): string;
```

### 描述

 方法返回一个由替换值（replacement）替换一些或所有匹配的模式（pattern）后的新字符串。
 模式可以是一个字符串或者一个正则表达式，替换值可以是一个字符串或者一个每次匹配都要调用的回调函数。

- 第一个参数可以是字符串，也可以是正则表达式

- 第二个参数可以是字符串，或者是函数(返回要匹配的字符串)

### 当第二个参数是字符串时，可以使用如下表格中的特殊变量

变量名 | 代表的值
-|-
$$ | 插入一个 "$"
$& | 插入匹配的子串
$` | 插入当前匹配的子串左边的内容
$' | 插入当前匹配的子串右边的内容。
$n | 假如第一个参数是 RegExp对象，并且 n 是个小于100的非负整数，那么插入第 n 个括号匹配的字符串。提示：索引是从1开始

### 示例

```js
const p = 'This is problem';
p.replace('problem', 'apple'); // This is apple
p.replace(/s/g, 'apple'); // Thiapple iapple problem
p.replace(/s/g, (a) => a+1); // This1 is1 problem
p.replace(); // This is problem
p.replace(/(\w+) is (\w+)/, '$2'); // problem
```