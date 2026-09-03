---
title: "NodeList: entries() method"
short-title: entries()
slug: Web/API/NodeList/entries
page-type: web-api-instance-method
browser-compat: api.NodeList.entries
---

{{APIRef("DOM")}}

متد **`NodeList.entries()`** یک {{jsxref("Iteration_protocols","iterator")}} بازمی‌گرداند که امکان پیمایش همهٔ جفت‌های کلید/مقدار موجود در این شیء را فراهم می‌کند. مقادیر، اشیاء {{domxref("Node")}} هستند.

## سینتکس

```js-nolint
entries()
```

### پارامترها

هیچ پارامتری.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator")}} بازمی‌گرداند.

## مثال

```js
const node = document.createElement("div");
const kid1 = document.createElement("p");
const kid2 = document.createTextNode("hey");
const kid3 = document.createElement("span");
node.appendChild(kid1);
node.appendChild(kid2);
node.appendChild(kid3);

const list = node.childNodes;

// Using for...of
for (const entry of list.entries()) {
  console.log(entry);
}
```

خروجی به این صورت است:

```plain
Array [ 0, <p> ]
Array [ 1, #text "hey" ]
Array [ 2, <span> ]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پالیفیل `NodeList.prototype.entries` در `core-js`](https://github.com/zloirock/core-js#iterable-dom-collections)
- {{domxref("Node")}}
- {{domxref("NodeList")}}