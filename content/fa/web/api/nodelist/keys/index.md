---
title: "NodeList: keys() method"
---

---
title: "NodeList: keys() method"
short-title: keys()
slug: Web/API/NodeList/keys
page-type: web-api-instance-method
browser-compat: api.NodeList.keys
---

{{APIRef("DOM")}}

متد **`NodeList.keys()`** یک {{jsxref("Iteration_protocols",'iterator')}} (تکرارگر) برمی‌گرداند که امکان پیمایش همه کلیدهای موجود در این شیء را فراهم می‌کند. کلیدها از نوع `unsigned integer` هستند.

## نحو

```js-nolint
keys()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator")}} (تکرارگر) برمی‌گرداند.

## مثال

```js
const node = document.createElement("div");
const kid1 = document.createElement("p");
const kid2 = document.createTextNode("hey");
const kid3 = document.createElement("span");

node.appendChild(kid1);
node.appendChild(kid2);
node.appendChild(kid3);

let list = node.childNodes;

// Using for...of
for (const key of list.keys()) {
  console.log(key);
}
```

نتیجه به صورت زیر است:

```plain
0
1
2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [پلی‌فیل `NodeList.prototype.keys` در `core-js`](https://github.com/zloirock/core-js#iterable-dom-collections)
- {{domxref("Node")}}
- {{domxref("NodeList")}}