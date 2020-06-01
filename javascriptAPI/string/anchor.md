# anchor()

## 语法

```ts
anchor(str: string | number): string;
big(): string;
bold(): string;
small(): string;
```

## 描述

- `anchor` 创建锚点(a)节点

- `big` 创建big标签

- `bold` 创建bold标签

- `small` 创建small标签


## 示例

```js
let str = 'Test';
str.anchor('demo'); // <a name="demo">Test</a>
str.big(); // <big>Test</big>
str.bold(); // <b>Test</b>
str.small(); // <small>Test</small>
```