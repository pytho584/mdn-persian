---
title: "Element: ariaLabel property"
short-title: ariaLabel
slug: Web/API/Element/ariaLabel
page-type: web-api-instance-property
browser-compat: api.Element.ariaLabel
---

{{APIRef("DOM")}}

خاصیت **`ariaLabel`** از رابط {{domxref("Element")}}، مقدار ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) را منعکس می‌کند که یک رشته برچسب‌گذار برای عنصر جاری تعریف می‌کند.

## مقدار

یک رشته یا `null`.

## مثال‌ها

در این مثال، ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) روی عنصری با شناسه `close-button` به "Close" تنظیم شده است. با استفاده از `ariaLabel` مقدار را به "Close dialog" به‌روز می‌کنیم.

```html
<button aria-label="Close" id="close-button">X</button>
```

```js
let el = document.getElementById("close-button");
console.log(el.ariaLabel); // "Close"
el.ariaLabel = "Close dialog";
console.log(el.ariaLabel); // "Close dialog"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}