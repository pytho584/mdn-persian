---
title: "DocumentType: replaceWith() method"
short-title: replaceWith()
slug: Web/API/DocumentType/replaceWith
page-type: web-api-instance-method
browser-compat: api.DocumentType.replaceWith
---

{{APIRef("DOM")}}

متد **`DocumentType.replaceWith()`** نوع سند را با مجموعه‌ای از گره‌های داده‌شده جایگزین می‌کند.

## نحو

```js-nolint
replaceWith(node1)
replaceWith(node1, node2)
replaceWith(node1, node2, /* …, */ nodeN)
```

### پارامترها

- `node1`، …، `nodeN`
  - : مجموعه‌ای از گره‌ها که قرار است {{domxref("DocumentType")}} با آن‌ها جایگزین شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره نتواند در نقطه مشخص‌شده در سلسله‌مراتب درج شود.

## مثال‌ها

### استفاده از `replaceWith()`

```js
let svgDt = document.implementation.createDocumentType(
  "svg:svg",
  "-//W3C//DTD SVG 1.1//EN",
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd",
);

document.doctype.replaceWith(svgDt);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.replaceWith()")}}
- {{domxref("Element.replaceWith()")}}
- {{domxref("CharacterData.replaceWith()")}}