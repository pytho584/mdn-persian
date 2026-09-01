---
title: "Document: childElementCount property"
short-title: childElementCount
slug: Web/API/Document/childElementCount
page-type: web-api-instance-property
browser-compat: api.Document.childElementCount
---

{{ APIRef("DOM") }}

خاصیت فقط‌خواندنی **`Document.childElementCount`** تعداد عناصر فرزند سند را برمی‌گرداند.

برای دریافت تعداد فرزندان یک عنصر خاص، به {{domxref("Element.childElementCount")}} مراجعه کنید.

## مقدار

یک عدد.

## مثال‌ها

```js
document.children;
// HTMLCollection، معمولاً شامل یک عنصر <html> است که تنها فرزند سند است

document.childElementCount;
// 1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.childElementCount")}}
- {{domxref("DocumentFragment.childElementCount")}}