---
title: "HTMLSelectElement: options property"
short-title: options
slug: Web/API/HTMLSelectElement/options
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.options
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`HTMLSelectElement.options`** یک {{domxref("HTMLOptionsCollection")}} از عناصر {{HTMLElement("option")}} موجود در عنصر {{HTMLElement("select")}} را بازمی‌گرداند.

## مقدار

یک {{domxref("HTMLOptionsCollection")}} شامل عناصر `<option>` موجود در عنصر `<select>`.

## مثال‌ها

### HTML

```html
<label for="test">Label</label>
<select id="test">
  <option value="1">Option 1</option>
  <option value="2">Option 2</option>
</select>
```

### JavaScript

```js
const select = document.getElementById("test");
for (const option of select.options) {
  console.log(option.label); // "Option 1" and "Option 2"
}
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}