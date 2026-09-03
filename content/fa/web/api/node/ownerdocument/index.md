---
title: "Node: ownerDocument property"
short-title: ownerDocument
slug: Web/API/Node/ownerDocument
page-type: web-api-instance-property
browser-compat: api.Node.ownerDocument
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`ownerDocument`** در رابط {{domxref("Node")}}، شیء سند سطح بالای آن گره را برمی‌گرداند.

## مقدار

یک {{domxref("Document")}} که شیء سطح بالایی است که همهٔ گره‌های فرزند در آن ایجاد شده‌اند.

اگر این ویژگی روی گره‌ای استفاده شود که خودش یک سند است، مقدار آن `null` خواهد بود.

## مثال

```js
// Given a node "p", get the top-level HTML
// child of the document object

const d = p.ownerDocument;
const html = d.documentElement;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}