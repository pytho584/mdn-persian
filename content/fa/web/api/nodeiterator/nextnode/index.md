---
title: "NodeIterator: nextNode() method"
short-title: nextNode()
slug: Web/API/NodeIterator/nextNode
page-type: web-api-instance-method
browser-compat: api.NodeIterator.nextNode
---

{{APIRef("DOM")}}

متد **`NodeIterator.nextNode()`** گرهٔ بعدی را در مجموعهٔ نمایش‌داده‌شده توسط {{domxref("NodeIterator")}} برمی‌گرداند و موقعیت تکرارگر را در این مجموعه به جلو می‌برد. اولین فراخوانیِ `nextNode()`، اولین گرهٔ مجموعه را برمی‌گرداند.

این متد وقتی هیچ گره‌ای در مجموعه باقی نمانده باشد، مقدار `null` را برمی‌گرداند.

در مرورگرهای قدیمی، آن‌گونه که در نسخه‌های قدیمی مشخصات تعیین شده بود، اگر این متد پس از فراخوانی {{domxref("NodeIterator.detach()")}} صدا زده می‌شد، ممکن بود استثنای `INVALID_STATE_ERR` از نوع {{domxref("DOMException")}} پرتاب شود. مرورگرهای به‌روز هرگز چنین استثنایی را پرتاب نمی‌کنند.

## سینتکس

```js-nolint
nextNode()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{domxref("Node")}} که گرهٔ بعد از گرهٔ جاری را در مجموعه‌ای که این `NodeIterator` نشان می‌دهد نمایش می‌دهد؛ یا اگر گرهٔ جاری آخرین گرهٔ مجموعه باشد، مقدار `null`.

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
currentNode = nodeIterator.nextNode(); // returns the next node
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابطی که این متد به آن تعلق دارد: {{domxref("NodeIterator")}}.