---
title: "Element: ariaPressed property"
short-title: ariaPressed
slug: Web/API/Element/ariaPressed
page-type: web-api-instance-property
browser-compat: api.Element.ariaPressed
---

{{APIRef("DOM")}}

خاصیت **`ariaPressed`** از رابط {{domxref("Element")}} منعکس‌کننده مقدار صفت [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) است که وضعیت فعلی «فشرده» دکمه‌های تغییر وضعیت (toggle buttons) را نشان می‌دهد.

> [!NOTE]
> در صورت امکان از عنصر HTML {{htmlelement("input")}} با `type="button"` یا عنصر {{htmlelement("button")}} استفاده کنید، زیرا اینها دارای معناشناسی داخلی هستند و نیازی به صفات ARIA ندارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر فشرده شده است.
- `"false"`
  - : عنصر قابلیت فشرده شدن را دارد اما در حال حاظر فشرده نشده است.
- `"mixed"`
  - : نشان‌دهنده یک مقدار حالت مختلط برای یک دکمه تغییر وضعیت سه‌حالته است.
- `"undefined"`
  - : عنصر قابلیت فشرده شدن را ندارد.

## مثال‌ها

در این مثال، صفت `aria-pressed` روی عنصری با شناسه `saveChanges` روی "false" تنظیم شده است که نشان می‌دهد این ورودی در حال حاظر فشرده نشده است. با استفاده از `ariaPressed` مقدار را به "true" به‌روزرسانی می‌کنیم.

```html
<div id="saveChanges" tabindex="0" role="button" aria-pressed="false">Save</div>
```

```js
let el = document.getElementById("saveChanges");
console.log(el.ariaPressed); // "false"
el.ariaPressed = "true";
console.log(el.ariaPressed); // "true"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نقش دکمه در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)