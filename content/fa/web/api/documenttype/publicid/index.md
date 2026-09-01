---
title: "DocumentType: publicId property"
---

---
title: "DocumentType: publicId property"
short-title: publicId
slug: Web/API/DocumentType/publicId
page-type: web-api-instance-property
browser-compat: api.DocumentType.publicId
---

{{APIRef("DOM")}}

ویژگی فقطخواندنی **`publicId`** در {{domxref("DocumentType")}} یک شناسهٔ رسمی سند را بازمی‌گرداند.

برای `DocumentType` مصنوعی، این ویژگی مقداری را که به‌عنوان پارامتر به {{domxref("DOMImplementation.createDocumentType()")}} داده شده است منعکس می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```js
const docType = document.implementation.createDocumentType(
  "svg",
  "-//W3C//DTD SVG 1.1//EN",
  "http://www.w3.org/2000/svg",
);

console.log(docType.publicId); // Displays "-//W3C//DTD SVG 1.1//EN"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}