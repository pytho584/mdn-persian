---
title: "HTMLEmbedElement: getSVGDocument() method"
---

---
title: "HTMLEmbedElement: getSVGDocument() method"
short-title: getSVGDocument()
slug: Web/API/HTMLEmbedElement/getSVGDocument
page-type: web-api-instance-method
browser-compat: api.HTMLEmbedElement.getSVGDocument
---

{{APIRef("HTML DOM")}}

روش **`getSVGDocument()`** از رابط {{domxref("HTMLEmbedElement")}}، شیء {{domxref("Document")}} مربوط به SVG تعبیه‌شده را بازمی‌گرداند.

## نحو

```js-nolint
getSVGDocument()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("Document")}}.

## مثال‌ها

```js
const svg = document.getElementById("el").getSVGDocument();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLIFrameElement.getSVGDocument")}}
- {{domxref("HTMLObjectElement.getSVGDocument")}}