---
title: "DOMImplementation: createDocumentType() method"
short-title: createDocumentType()
slug: Web/API/DOMImplementation/createDocumentType
page-type: web-api-instance-method
browser-compat: api.DOMImplementation.createDocumentType
---

{{ ApiRef("DOM")}}

متد **`DOMImplementation.createDocumentType()`** یک شیء {{domxref("DocumentType")}} بازمی‌گرداند که می‌تواند در زمان ایجاد سند با {{domxref("DOMImplementation.createDocument")}} استفاده شود یا از طریق روش‌هایی مانند {{domxref("Node.insertBefore()")}} یا {{domxref("Node.replaceChild()")}} در سند قرار گیرد.

## نحو

```js-nolint
createDocumentType(name, publicId, systemId)
```

### پارامترها

- `name`
  - : یک رشته شامل نام نوع سند (doctype)، مانند `html`. معادل ویژگی {{domxref("DocumentType.name")}} است.
- `publicId`
  - : یک رشته شامل شناسه `PUBLIC`. معادل ویژگی {{domxref("DocumentType.publicId")}} است.
- `systemId`
  - : یک رشته شامل شناسه `SYSTEM`. معادل ویژگی {{domxref("DocumentType.systemId")}} است.

### مقدار بازگشتی

یک [`DocumentType`](/en-US/docs/Web/API/DocumentType).

## مثال‌ها

```js
const dt = document.implementation.createDocumentType(
  "svg",
  "-//W3C//DTD SVG 1.1//EN",
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd",
);
const d = document.implementation.createDocument(
  "http://www.w3.org/2000/svg",
  "svg:svg",
  dt,
);
console.log(d.doctype.publicId); // -//W3C//DTD SVG 1.1//EN
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رَابط {{domxref("DOMImplementation")}} که این متد به آن تعلق دارد.