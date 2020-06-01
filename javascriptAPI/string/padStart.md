# padStart()

## 语法

```ts
padStart(targetLength: number, padString: string): string;
```

## 描述

 方法用另一个字符串填充当前字符串(重复，如果需要的话)，以便产生的字符串达到给定的长度。填充从当前字符串的开始(左侧)应用的。

- `targetLength`当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。

- `padString`填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）

## 示例

```js
let str = 'testpadStart';
str.padStart(15, '12'); // 121testpadStart
str.padEnd(); // testpadStart
str.padEnd(15); // "   testpadStart"
```