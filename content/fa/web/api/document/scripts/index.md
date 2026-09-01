---
title: "Document: scripts property"
short-title: scripts
slug: Web/API/Document/scripts
page-type: web-api-instance-property
browser-compat: api.Document.scripts
---

{{APIRef("DOM")}}

خاصیت **`scripts`** از رابط {{domxref("Document")}} فهرستی از عناصر {{HTMLElement("script")}} در سند را برمی‌گرداند. شیء برگشتی یک {{domxref("HTMLCollection")}} است.

## مقدار

یک {{domxref("HTMLCollection")}}. می‌توانید از آن مانند یک آرایه برای دریافت تمام عناصر موجود در فهرست استفاده کنید.

## مثال‌ها

این مثال بررسی می‌کند که آیا صفحه دارای هرگونه عنصر {{HTMLElement("script")}} است یا خیر.

```js
let scripts = document.scripts;

if (scripts.length) {
  alert("This page has scripts!");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}