---
title: "NodeIterator: detach() method"
short-title: detach()
slug: Web/API/NodeIterator/detach
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.NodeIterator.detach
---

{{APIRef("DOM")}}{{deprecated_header}}

متد **`NodeIterator.detach()`** یک عملیات بدون اثر (no-op) است که تنها برای سازگاری با نسخه‌های قبلی نگه داشته شده است.

در ابتدا، این متد {{domxref("NodeIterator")}} را از مجموعه‌ای که روی آن تکرار می‌کند جدا می‌کرد، منابع استفاده شده توسط مجموعه را آزاد می‌کرد و وضعیت پیمایش‌گر را به `INVALID` تنظیم می‌نمود. پس از فراخوانی این متد، فراخوانی سایر متدهای `NodeIterator` باعث ایجاد استثنای `INVALID_STATE_ERR` می‌شد.

## نحو

```js-nolint
detach()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

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
nodeIterator.detach(); // detaches the iterator

nodeIterator.nextNode(); // throws an INVALID_STATE_ERR exception
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که به آن تعلق دارد: {{domxref("NodeIterator")}}.