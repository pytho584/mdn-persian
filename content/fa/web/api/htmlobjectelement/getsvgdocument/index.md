---
title: "HTMLObjectElement: getSVGDocument() method"
short-title: getSVGDocument()
slug: Web/API/HTMLObjectElement/getSVGDocument
page-type: web-api-instance-method
browser-compat: api.HTMLObjectElement.getSVGDocument
---

{{APIRef("HTML DOM")}}

متد **`getSVGDocument()`** از رابط {{domxref("HTMLObjectElement")}}، شیء {{domxref("Document")}} مربوط به SVG تعبیه‌شده را برمی‌گرداند.

## سینتکس

```js-nolint
getSVGDocument()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("Document")}}.

## مثال‌ها

```js
const svg = document.getElementById("el").getSVGDocument();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLIFrameElement.getSVGDocument")}}
- {{domxref("HTMLEmbedElement.getSVGDocument")}}