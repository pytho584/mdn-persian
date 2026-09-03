---
title: "NodeIterator: referenceNode property"
---

---
title: "NodeIterator: referenceNode property"
short-title: referenceNode
slug: Web/API/NodeIterator/referenceNode
page-type: web-api-instance-property
browser-compat: api.NodeIterator.referenceNode
---

{{APIRef("DOM")}}

خاصیت فقطخواندنی **`NodeIterator.referenceNode`**، {{domxref("Node")}}ای را برمی‌گرداند که تکرارکننده به آن متصل است؛ با درج شدن گره‌های جدید، تکرارکننده همان‌طور که توسط این خاصیت تعیین شده، به گره مرجع متصل باقی می‌ماند.

## مقدار

یک {{domxref("Node")}}.

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
node = nodeIterator.referenceNode;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- واسطی که این خاصیت به آن تعلق دارد: {{domxref("NodeIterator")}}