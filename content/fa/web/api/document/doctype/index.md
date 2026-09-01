---
title: "Document: doctype property"
short-title: doctype
slug: Web/API/Document/doctype
page-type: web-api-instance-property
browser-compat: api.Document.doctype
---

{{ApiRef("DOM")}}

ویژگی فقط‌خواندنی **`doctype`** در رابط {{domxref("Document")}} یک شیء {{domxref("DocumentType")}} است که {{glossary("Doctype", "Document Type Declaration (DTD)")}} مرتبط با سند کنونی را نمایش می‌دهد.

## مقدار

یک شیء {{domxref("DocumentType")}}.

## نمونه‌ها

```js
const doctypeObj = document.doctype;

console.log(`doctypeObj.name: ${doctypeObj.name}`);
console.log(`doctypeObj.internalSubset: ${doctypeObj.internalSubset}`);
console.log(`doctypeObj.publicId: ${doctypeObj.publicId}`);
console.log(`doctypeObj.systemId: ${doctypeObj.systemId}`);
```

## یادداشت‌ها

اگر هیچ DTD مرتبط با سند کنونی وجود نداشته باشد، این ویژگی `null` برمی‌گرداند.

DOM Level 2 از ویرایش اعلامیه نوع سند (Document Type Declaration) پشتیبانی نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}