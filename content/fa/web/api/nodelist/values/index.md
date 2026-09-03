---
title: "NodeList: values() method"
short-title: values()
slug: Web/API/NodeList/values
page-type: web-api-instance-method
browser-compat: api.NodeList.values
---

{{APIRef("DOM")}}

متد **`NodeList.values()`** یک {{jsxref("Iteration_protocols",'iterator')}} برمی‌گرداند که امکان پیمایش روی همهٔ مقادیر موجود در این شیء را فراهم می‌کند. این مقادیر، اشیاء {{domxref("Node")}} هستند.

## سینتکس

```js-nolint
values()
```

### پارامترها

هیچ.

### مقدار برگشتی

یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند.

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
for (const value of list.values()) {
  console.log(value);
}
```

نتیجه به این صورت است:

```plain
<p>
#text "hey"
<span>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [پالیفیلِ `NodeList.prototype.values` در `core-js`](https://github.com/zloirock/core-js#iterable-dom-collections)
- {{domxref("Node")}}
- {{domxref("NodeList")}}