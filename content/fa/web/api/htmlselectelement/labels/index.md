---
title: "HTMLSelectElement: labels property"
---

---
title: "HTMLSelectElement: labels property"
short-title: labels
slug: Web/API/HTMLSelectElement/labels
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.labels
---

{{APIRef("DOM")}}

ویژگی فقطخواندنی **`HTMLSelectElement.labels`** یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر {{HTMLElement("select")}} را برمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل عناصر `<label>` مرتبط با عنصر `<select>`.

## مثال‌ها

### HTML

```html
<label id="label1" for="test">Label 1</label>
<select id="test">
  <option value="1">Option 1</option>
  <option value="2">Option 2</option>
</select>
<label id="label2" for="test">Label 2</label>
```

### JavaScript

```js
const select = document.getElementById("test");
for (const label of select.labels) {
  console.log(label.textContent); // "Label 1" and "Label 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}