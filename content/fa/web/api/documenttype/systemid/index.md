---
title: "DocumentType: systemId property"
short-title: systemId
slug: Web/API/DocumentType/systemId
page-type: web-api-instance-property
browser-compat: api.DocumentType.systemId
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`systemId`** از رابط {{domxref("DocumentType")}}، URL مربوط به DTD مرتبط را بازمی‌گرداند.

برای `DocumentType`های مصنوعی، این ویژگی مقدار داده‌شده به عنوان پارامتر در {{domxref("DOMImplementation.createDocumentType()")}} را منعکس می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```js
const docType = document.implementation.createDocumentType(
  "svg",
  "",
  "http://www.w3.org/2000/svg",
);

console.log(docType.systemId); // نمایش می‌دهد "http://www.w3.org/2000/svg"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}