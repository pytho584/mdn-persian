---
title: "Document: all property"
short-title: all
slug: Web/API/Document/all
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.Document.all
---

{{APIRef("DOM")}}{{Deprecated_Header}}

خاصیت **`all`** فقط خواندنی (read-only) از رابط (interface) {{DOMxRef("Document")}} یک {{DOMxRef("HTMLAllCollection")}} برمی‌گرداند که ریشه در گره سند (document node) دارد.

به جای استفاده از `document.all` برای دریافت یک {{DOMxRef("HTMLAllCollection")}} از تمام عناصر سند به ترتیب سند (document order)، می‌توانید از {{DOMxRef("Document.querySelectorAll")}} استفاده کنید تا یک {{DOMxRef("NodeList")}} از تمام عناصر سند به ترتیب سند دریافت کنید:

```js
const allElements = document.querySelectorAll("*");
```

## مقدار

یک {{DOMxRef("HTMLAllCollection")}} که شامل تمام عناصر موجود در سند است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}