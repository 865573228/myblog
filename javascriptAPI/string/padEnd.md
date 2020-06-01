# padEnd()

## 语法

```ts
padEnd(targetLength: number, padString: string): string;
```

## 描述

 方法会用一个字符串填充当前字符串（如果需要的话则重复填充），返回填充后达到指定长度的字符串。从当前字符串的末尾（右侧）开始填充。

- `targetLength`当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。

- `padString`填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）

## 示例

```js
let str = 'testpadEnd';
str.padEnd(12, '12'); // testpadEnd12
str.padEnd(); // testpadEnd
str.padEnd(12); // "testpadEnd  "
```