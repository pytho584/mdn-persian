---
title: "NodeIterator: root property"
short-title: root
slug: Web/API/NodeIterator/root
page-type: web-api-instance-property
browser-compat: api.NodeIterator.root
---

{{APIRef("DOM")}}

خاصیت فقط‑خواندنی **`NodeIterator.root`** گره‌ای ({{DOMxref("Node")}}) را نشان می‌دهد که ریشهٔ چیزی است که {{DOMxref("NodeIterator")}} آن را پیمایش می‌کند.

## مقدار

یک {{DOMxref("Node")}}.

## نمونه‌ها

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
root = nodeIterator.root; // در اینجا document.body
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- واسطی که این ویژگی به آن تعلق دارد: {{domxref("NodeIterator")}}.