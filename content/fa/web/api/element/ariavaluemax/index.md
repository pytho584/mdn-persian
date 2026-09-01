---
title: "Element: ariaValueMax property"
short-title: ariaValueMax
slug: Web/API/Element/ariaValueMax
page-type: web-api-instance-property
browser-compat: api.Element.ariaValueMax
---

{{APIRef("DOM")}}

ویژگی **`ariaValueMax`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) را منعکس می‌کند که حداکثر مقدار مجاز را برای یک ویجت محدوده (range widget) تعریف می‌کند.

## مقدار

رشته‌ای (string) که شامل یک عدد است.

## مثال‌ها

در این مثال، ویژگی [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) روی عنصری با شناسه `slider` برابر با «7» تنظیم شده است. با استفاده از `ariaValueMax` مقدار آن را به «6» تغییر می‌دهیم.

```html
<div
  role="slider"
  aria-valuenow="1"
  aria-valuemin="1"
  aria-valuemax="7"
  aria-valuetext="Sunday"></div>
```

```js
let el = document.getElementById("slider");
console.log(el.ariaValueMax); // 7
el.ariaValueMax = "6";
console.log(el.ariaValueMax); // 6
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}