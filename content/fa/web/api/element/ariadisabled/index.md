---
title: "Element: ariaDisabled property"
short-title: ariaDisabled
slug: Web/API/Element/ariaDisabled
page-type: web-api-instance-property
browser-compat: api.Element.ariaDisabled
---

{{APIRef("DOM")}}

ویژگی **`ariaDisabled`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) است که نشان می‌دهد عنصر قابل درک (perceivable) است اما غیرفعال است، بنابراین قابل ویرایش یا تعامل نیست.

> [!NOTE]
> در صورت امکان، از عنصر {{htmlelement("input")}} با `type="button"` یا عنصر {{htmlelement("button")}} استفاده کنید — زیرا این عناصر دارای معناشناسی داخلی هستند و به ویژگی‌های ARIA نیازی ندارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر و همهٔ فرزندان قابل فوکوس‌شونده غیرفعال هستند، اما قابل درک‌اند و کاربر نمی‌تواند مقادیر آن‌ها را تغییر دهد.
- `"false"`
  - : عنصر فعال است.

## مثال‌ها

در این مثال، ویژگی `aria-disabled` روی عنصری با شناسهٔ `saveChanges` برابر با «true» تنظیم شده است که نشان می‌دهد این ورودی در حال حاضر غیرفعال است. با استفاده از `ariaDisabled` مقدار را به «false» تغییر می‌دهیم.

```html
<div id="saveChanges" tabindex="0" role="button" aria-disabled="true">Save</div>
```

```js
let el = document.getElementById("saveChanges");
console.log(el.ariaDisabled); // "true"
el.ariaDisabled = "false";
console.log(el.ariaDisabled); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}