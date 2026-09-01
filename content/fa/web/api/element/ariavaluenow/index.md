---
title: "Element: ariaValueNow property"
short-title: ariaValueNow
slug: Web/API/Element/ariaValueNow
page-type: web-api-instance-property
browser-compat: api.Element.ariaValueNow
---

{{APIRef("DOM")}}

ویژگی **`ariaValueNow`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) را بازتاب می‌دهد که مقدار فعلی یک ابزارک دامنه (range widget) را تعریف می‌کند.

## مقدار

یک رشته (string) که شامل یک عدد است.

## مثال‌ها

در این مثال، ویژگی [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) روی عنصری با شناسه `slider` برابر با «1» تنظیم شده است. با استفاده از `ariaValueNow` مقدار را به «2» به‌روزرسانی می‌کنیم.

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
console.log(el.ariaValueNow); // 1
el.ariaValueNow = "2";
console.log(el.ariaValueNow); // 2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}