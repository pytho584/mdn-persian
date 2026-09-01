---
title: "Element: ariaModal property"
short-title: ariaModal
slug: Web/API/Element/ariaModal
page-type: web-api-instance-property
browser-compat: api.Element.ariaModal
---

{{APIRef("DOM")}}

ویژگی **`ariaModal`** از رابط {{domxref("Element")}} مقدار ویژگی `aria-modal` را منعکس می‌کند که نشان می‌دهد آیا یک عنصر هنگام نمایش مودال است یا خیر. اعمال ویژگی `aria-modal` به یک عنصر با `role="dialog"` جایگزین روش استفاده از `aria-hidden` در پس‌زمینه برای اطلاع‌رسانی به فناوری‌های کمکی می‌شود که محتوای خارج از دیالوگ غیرفعال است.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`: عنصر مودال است.
- `"false"`: عنصر مودال نیست.

## مثال‌ها

در این مثال، ویژگی `aria-modal` روی عنصری با شناسه `address-modal` به `"true"` تنظیم شده است که نشان می‌دهد این یک دیالوگ مودال است. با استفاده از `ariaModal` مقدار را به `"false"` به‌روز می‌کنیم.

```html
<div
  role="dialog"
  id="address-modal"
  aria-labelledby="dialog1Title"
  aria-describedby="dialog1Desc"
  aria-modal="true"></div>
```

```js
let el = document.getElementById("address-modal");
console.log(el.ariaModal); // "true"
el.ariaModal = "false";
console.log(el.ariaModal); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [ARIA: dialog role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)