---
title: "NodeIterator: pointerBeforeReferenceNode property"
---

{{APIRef("DOM")}}

ویژگی فقط‑خواندنی **`NodeIterator.pointerBeforeReferenceNode`** یک پرچم بولی (Boolean) برمی‌گرداند که نشان می‌دهد آیا `NodeFilter` قبل از گره لنگر (anchor node) که توسط ویژگی {{domxref("NodeIterator.referenceNode")}} مشخص شده است، لنگر انداخته (اگر این مقدار `true` باشد) یا بعد از آن (اگر این مقدار `false` باشد).

## مقدار

یک مقدار بولی.

## مثال‌ها

```js
const nodeIterator = document.createNodeIterator(
  document.body,
  NodeFilter.SHOW_ELEMENT,
  {
    acceptNode(node) {
      return NodeFilter.FILTER_ACCEPT;
    },
  },
);
flag = nodeIterator.pointerBeforeReferenceNode;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که به آن تعلق دارد: {{domxref("NodeIterator")}}