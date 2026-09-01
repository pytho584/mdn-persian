---
title: "Element: ariaAtomic property"
short-title: ariaAtomic
slug: Web/API/Element/ariaAtomic
page-type: web-api-instance-property
browser-compat: api.Element.ariaAtomic
---

{{APIRef("DOM")}}

ویژگی **`ariaAtomic`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است. این ویژگی مشخص می‌کند که آیا فناوری‌های کمکی بر اساس اعلان‌های تغییر تعریف‌شده توسط ویژگی [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant)، کل ناحیهٔ تغییر یافته را ارائه می‌دهند یا فقط بخش‌هایی از آن را.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"false"`
  - : فناوری‌های کمکی فقط گره (node) یا گره‌های تغییریافته را ارائه می‌دهند.
- `"true"`
  - : فناوری‌های کمکی کل ناحیهٔ تغییر یافته را به‌صورت یکپارچه ارائه می‌دهند، از جمله برچسب تعریف‌شده توسط نویسنده در صورت وجود.

## مثال‌ها

در این مثال، ویژگی `aria-atomic` روی عنصری که شناسهٔ آن `"clock"` است، روی `"true"` تنظیم شده است. با استفاده از `ariaAtomic` مقدار آن را به `"false"` تغییر می‌دهیم.

```html
<div id="clock" role="timer" aria-live="polite" aria-atomic="true"></div>
```

```js
let el = document.getElementById("clock");
console.log(el.ariaAtomic); // true
el.ariaAtomic = "false";
console.log(el.ariaAtomic); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}