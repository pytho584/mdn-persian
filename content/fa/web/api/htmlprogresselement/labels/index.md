---
title: "HTMLProgressElement: labels property"
short-title: labels
slug: Web/API/HTMLProgressElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLProgressElement.labels
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`HTMLProgressElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("progress")}} را برمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل عناصر `<label>` مرتبط با عنصر `<progress>`.

## مثال‌ها

### HTML

```html
<label id="label1" for="test">Label 1</label>
<progress id="test" value="70" max="100">70%</progress>
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const progress = document.getElementById("test");
for (const label of progress.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}