---
title: "Element: ariaHidden property"
---

---
title: "Element: ariaHidden property"
short-title: ariaHidden
slug: Web/API/Element/ariaHidden
page-type: web-api-instance-property
browser-compat: api.Element.ariaHidden
---

{{APIRef("DOM")}}

ویژگی **`ariaHidden`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)) را منعکس می‌کند که مشخص می‌کند آیا عنصر در معرض یک API دسترس‌پذیری قرار می‌گیرد یا نه.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر از API دسترس‌پذیری پنهان است.
- `"false"`
  - : عنصر به API دسترس‌پذیری ارائه می‌شود، گویی که رندر شده است.
- `"undefined"`
  - : وضعیت پنهان بودن عنصر توسط عامل کاربر (user agent) و بر اساس رندر شدن یا نشدن آن تعیین می‌شود.

## مثال‌ها

در این مثال، ویژگی [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) روی عنصری با شناسهٔ `hidden` روی «true» تنظیم شده است. با استفاده از `ariaHidden` مقدار را به «false» تغییر می‌دهیم.

```html
<div id="hidden" aria-hidden="true">Some things are better left unsaid.</div>
```

```js
let el = document.getElementById("hidden");
console.log(el.ariaHidden); // true
el.ariaHidden = "false";
console.log(el.ariaHidden); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}