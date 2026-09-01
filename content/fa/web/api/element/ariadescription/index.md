---
title: "Element: ariaDescription property"
short-title: ariaDescription
slug: Web/API/Element/ariaDescription
page-type: web-api-instance-property
browser-compat: api.Element.ariaDescription
---

{{APIRef("DOM")}}

ویژگی **`ariaDescription`** از رابط {{domxref("Element")}} منعکس‌کننده مقدار صفت [`aria-description`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-description) است که یک مقدار رشته‌ای را تعریف می‌کند که عنصر جاری را توصیف یا حاشیه‌نویسی می‌کند.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، صفت `aria-description` روی عنصری با شناسه `close-button` به رشته "A longer description of the function of this element" تنظیم شده است. با استفاده از `ariaDescription` می‌توانیم مقدار را به‌روزرسانی کنیم.

```html
<button
  aria-label="Close"
  aria-description="A longer description of the function of this element"
  id="close-button">
  X
</button>
```

```js
let el = document.getElementById("close-button");
console.log(el.ariaDescription); // "A longer description of the function of this element"
el.ariaDescription = "A different description";
console.log(el.ariaDescription); // "A different description"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}