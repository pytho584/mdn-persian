---
title: "HTMLOutputElement: labels property"
short-title: labels
slug: Web/API/HTMLOutputElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.labels
---

{{APIRef("DOM")}}

خاصیتِ فقط‌خواندنی **`HTMLOutputElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("output")}} بازمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل عناصر `<label>` مرتبط با عنصر `<output>`.

## مثال‌ها

### HTML

```html
<label id="label1" for="test">Label 1</label>
<output id="test">Output</output>
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const output = document.getElementById("test");
for (const label of output.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}