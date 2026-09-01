---
title: "HTMLIFrameElement: getSVGDocument() method"
short-title: getSVGDocument()
slug: Web/API/HTMLIFrameElement/getSVGDocument
page-type: web-api-instance-method
browser-compat: api.HTMLIFrameElement.getSVGDocument
---

{{APIRef("HTML DOM")}}

متد **`getSVGDocument()`** در رابط {{domxref("HTMLIFrameElement")}}، شیء {{domxref("Document")}} مربوط به SVG تعبیه‌شده را بازمی‌گرداند.

## نحو

```js-nolint
getSVGDocument()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{domxref("Document")}}.

## مثال‌ها

```js
const svgDoc = document.getElementById("el").getSVGDocument();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLEmbedElement.getSVGDocument")}}
- {{domxref("HTMLObjectElement.getSVGDocument")}}