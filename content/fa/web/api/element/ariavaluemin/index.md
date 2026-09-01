---
title: "Element: ariaValueMin property"
short-title: ariaValueMin
slug: Web/API/Element/ariaValueMin
page-type: web-api-instance-property
browser-compat: api.Element.ariaValueMin
---

{{APIRef("DOM")}}

ویژگی **`ariaValueMin`** از رابط (interface) {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) است که کمترین مقدار مجاز را برای یک ویجت محدوده (range widget) تعریف می‌کند.

## مقدار

یک رشته (string) که شامل یک عدد است.

## مثال‌ها

در این مثال، ویژگی `aria-valuemin` روی عنصری با شناسه `slider` به "1" تنظیم شده است. با استفاده از `ariaValueMin` مقدار را به "2" به‌روز می‌کنیم.

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
console.log(el.ariaValueMin); // 1
el.ariaValueMin = "2";
console.log(el.ariaValueMin); // 2
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}