# localeCompare()

## 语法

```ts
localeCompare(str: string, locales?: string): number;
```

## 描述

用本地特定的顺序来比较两个字符串。

- `str`表示用来比较的字符串

- 常用于本地排序

## 示例

```js
'a'.localeCompare('b'); // -1
'b'.localeCompare('a'); // 1
'b'.localeCompare('b'); // 0
```