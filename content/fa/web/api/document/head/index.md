---
title: "Document: head property"
short-title: head
slug: Web/API/Document/head
page-type: web-api-instance-property
browser-compat: api.Document.head
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`head`** در رابط {{domxref("Document")}}، عنصر {{HTMLElement("head")}} سند جاری را بازمی‌گرداند.

## مقدار

یک {{domxref("HTMLHeadElement")}}.

## مثال‌ها

```html
<!doctype html>
<head id="my-document-head">
  <title>Example: using document.head</title>
</head>
```

```js
const theHead = document.head;

console.log(theHead.id); // "my-document-head";
console.log(theHead === document.querySelector("head")); // true
```

## نکات

`document.head` فقط‌خواندنی است. تلاش برای مقداردهی به این ویژگی یا بی‌صدا شکست می‌خورد یا در [حالت سختگیرانه](/en-US/docs/Web/JavaScript/Reference/Strict_mode) یک {{jsxref("TypeError")}} پرتاب می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.body")}}