---
title: "Element: ariaKeyShortcuts property"
short-title: ariaKeyShortcuts
slug: Web/API/Element/ariaKeyShortcuts
page-type: web-api-instance-property
browser-compat: api.Element.ariaKeyShortcuts
---

{{APIRef("DOM")}}

ویژگی **`ariaKeyShortcuts`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی `aria-keyshortcuts` است. این ویژگی میانبرهای صفحه‌کلیدی را نشان می‌دهد که نویسنده برای فعال‌سازی یا دادن فوکوس به یک عنصر پیاده‌سازی کرده است.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، ویژگی `aria-keyshortcuts` روی عنصری با شناسهٔ `skip-link` به "Alt+Shift+A" تنظیم شده است. با استفاده از `ariaKeyShortcuts` مقدار را به "Alt+Shift+M" به‌روز می‌کنیم.

```html
<a id="skip-link" href="#content" aria-keyshortcuts="Alt+Shift+A">
  Skip to content
</a>
```

```js
let el = document.getElementById("saveChanges");
console.log(el.ariaKeyShortcuts); // "Alt+Shift+A"
el.ariaKeyShortcuts = "Alt+Shift+M";
console.log(el.ariaKeyShortcuts); // "Alt+Shift+M"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}