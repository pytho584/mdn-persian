---
title: "NodeIterator: previousNode() method"
short-title: previousNode()
slug: Web/API/NodeIterator/previousNode
page-type: web-api-instance-method
browser-compat: api.NodeIterator.previousNode
---

{{APIRef("DOM")}}

متد **`NodeIterator.previousNode()`** گره قبلی در مجموعه‌ای را که توسط {{domxref("NodeIterator")}} نمایش داده می‌شود، برمی‌گرداند و موقعیت پیمایشگر را درون مجموعه به عقب می‌برد.

این متد در صورتی که گره جاری اولین گره در مجموعه باشد، `null` برمی‌گرداند.

در مرورگرهای قدیمی، مطابق نسخه‌های قدیمی مشخصات، در صورت فراخوانی این متد پس از متد {{domxref("NodeIterator.detach()")}}، ممکن است استثنای `INVALID_STATE_ERR` {{domxref("DOMException")}} پرتاب شود. مرورگرهای جدید هیچگاه استثنا پرتاب نمی‌کنند.

## نحو

```js-nolint
previousNode()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("Node")}} که نشان‌دهنده گره قبل از گره جاری در مجموعه نمایش داده شده توسط این `NodeIterator` است، یا اگر گره جاری اولین گره در مجموعه باشد، `null` برمی‌گرداند.

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
currentNode = nodeIterator.nextNode(); // گره بعدی را برمی‌گرداند
previousNode = nodeIterator.previousNode(); // نتیجه مشابه، زیرا به گره قبلی بازگشته‌ایم
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که این متد به آن تعلق دارد: {{domxref("NodeIterator")}}.