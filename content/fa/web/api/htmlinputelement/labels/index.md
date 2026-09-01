---
title: "HTMLInputElement: labels property"
short-title: labels
slug: Web/API/HTMLInputElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.labels
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`HTMLInputElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("input")}} را برمی‌گرداند، به شرطی که عنصر مخفی نباشد. اگر نوع عنصر `hidden` باشد، این ویژگی `null` را برمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل عناصر `<label>` که با عنصر `<input>` مرتبط هستند.

## مثال‌ها

### HTML

```html
<label id="label1" for="test">Label 1</label>
<input id="test" />
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const input = document.getElementById("test");
for (const label of input.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}