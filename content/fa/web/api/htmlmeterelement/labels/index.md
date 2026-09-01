---
title: "HTMLMeterElement: labels property"
---

---
title: "HTMLMeterElement: labels property"
short-title: labels
slug: Web/API/HTMLMeterElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLMeterElement.labels
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`HTMLMeterElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("meter")}} را برمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل عناصر `<label>` مرتبط با عنصر `<meter>`.

## مثال‌ها

### HTML

```html
<label id="label1" for="test">Label 1</label>
<meter id="test" min="0" max="100" value="70">70</meter>
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const meter = document.getElementById("test");
for (const label of meter.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}