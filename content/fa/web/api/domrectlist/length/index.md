---
title: "DOMRectList: length property"
short-title: length
slug: Web/API/DOMRectList/length
page-type: web-api-instance-property
browser-compat: api.DOMRectList.length
---

{{APIRef("Geometry Interfaces")}}

ویژگی فقط‌خواندنی **`length`** در رابط {{domxref("DOMRectList")}} تعداد اشیای {{domxref("DOMRect")}} موجود در فهرست را بازمی‌گرداند.

## مقدار

یک عدد صحیح مثبت که تعداد اشیای `DOMRect` را در `DOMRectList` نشان می‌دهد. اگر هیچ مستطیلی در فهرست نباشد، `length` برابر `0` است.

## مثال‌ها

در مثال زیر، فهرست مستطیل‌های یک عنصر {{htmlelement("div")}} را با استفاده از {{domxref("Element.getClientRects()")}} دریافت می‌کنیم. سپس تعداد مستطیل‌های موجود در فهرست را در یک عنصر `<div>` دیگر در صفحه نمایش می‌دهیم.

ابتدا، HTML:

```html
<div id="box"></div>
<div id="output"></div>
```

```css
#box {
  width: 50px;
  height: 20px;
  border: 1px solid black;
}
```

حالا JavaScript:

```js
const box = document.getElementById("box");
const rects = box.getClientRects();
const output = document.getElementById("output");

output.textContent = `Number of rectangles: ${rects.length}`;
```

خروجی به این شکل است:

{{ EmbedLiveSample('Examples', '100%', 60) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}