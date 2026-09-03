---
title: "NodeIterator: filter property"
---

---
title: "NodeIterator: filter property"
short-title: filter
slug: Web/API/NodeIterator/filter
page-type: web-api-instance-property
browser-compat: api.NodeIterator.filter
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`NodeIterator.filter`** یک شیء `NodeFilter` برمی‌گرداند؛ شیئی که متدی به نام `acceptNode(node)` را پیاده‌سازی می‌کند و برای پالایش گره‌ها استفاده می‌شود.

هنگام ایجاد {{domxref("NodeIterator")}}، شیء فیلتر به‌عنوان پارامتر سوم ارسال می‌شود و متد `acceptNode(node)` روی تک‌تک گره‌ها فراخوانی می‌شود تا مشخص کند آیا آن گره پذیرفته شود یا نه. این تابع باید ثابت `NodeFilter.FILTER_ACCEPT` را در مواردی که گره باید پذیرفته شود و `NodeFilter.FILTER_REJECT` را در مواردی که گره باید رد شود برگرداند.

## مقدار

یک شیء `NodeFilter`.

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
nodeFilter = nodeIterator.filter;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که این ویژگی به آن تعلق دارد: {{domxref("NodeIterator")}}.