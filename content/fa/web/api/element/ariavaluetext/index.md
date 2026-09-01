---
title: "Element: ariaValueText property"
short-title: ariaValueText
slug: Web/API/Element/ariaValueText
page-type: web-api-instance-property
browser-compat: api.Element.ariaValueText
---

{{APIRef("DOM")}}

ویژگی **`ariaValueText`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext) است که متن جایگزین قابل‌خواندن برای انسان از `aria-valuenow` در یک ابزارک محدوده (range widget) را تعریف می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، ویژگی `aria-valuetext` روی عنصری با شناسه `slider` به «Sunday» تنظیم شده است تا یک مقدار قابل‌خواندن برای انسان برای محدوده ارائه دهد. با استفاده از `ariaValueText` مقدار را به «Monday» به‌روزرسانی می‌کنیم.

```html
<div
  id="slider"
  role="slider"
  aria-valuenow="1"
  aria-valuemin="1"
  aria-valuemax="7"
  aria-valuetext="Sunday"></div>
```

```js
let el = document.getElementById("slider");
console.log(el.ariaValueText); // Sunday
el.ariaValueText = "Monday";
console.log(el.ariaValueText); // Monday
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}