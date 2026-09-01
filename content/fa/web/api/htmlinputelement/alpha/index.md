---
title: "HTMLInputElement: alpha property"
short-title: alpha
slug: Web/API/HTMLInputElement/alpha
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLInputElement.alpha
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

ویژگی **`alpha`** در رابط {{domxref("HTMLInputElement")}} بازتاب‌دهندهٔ صفت [`alpha`](/en-US/docs/Web/HTML/Reference/Elements/input/color#alpha) عنصر {{htmlelement("input")}} است که نشان می‌دهد آیا مؤلفهٔ آلفای رنگ CSS توسط کاربر نهایی قابل تغییر است و آیا لازم است کاملاً مات باشد یا خیر. این ویژگی فقط برای کنترل‌های [color](/en-US/docs/Web/HTML/Reference/Elements/input/color) کاربرد دارد.

## مقدار

یک مقدار بولی.

## مثال‌ها

```html
<input id="color-picker" type="color" alpha />
```

```js
const colorInput = document.getElementById("color-picker");

if (colorInput.alpha) {
  // Color values contain an alpha component
} else {
  // We have fully opaque color values
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`<input type="color">`](/en-US/docs/Web/HTML/Reference/Elements/input/color)