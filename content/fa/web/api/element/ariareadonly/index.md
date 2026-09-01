---
title: "Element: ariaReadOnly property"
short-title: ariaReadOnly
slug: Web/API/Element/ariaReadOnly
page-type: web-api-instance-property
browser-compat: api.Element.ariaReadOnly
---

{{APIRef("DOM")}}

ویژگی **`ariaReadOnly`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) را منعکس می‌کند که نشان می‌دهد عنصر قابل ویرایش نیست، اما در سایر جنبه‌ها قابل استفاده است.

> [!NOTE]
> در صورت امکان، از عنصر HTML {{htmlelement("input")}} با `type="text"` یا {{htmlelement("textarea")}} استفاده کنید، زیرا این عناصر معنای داخلی دارند و به ویژگی‌های ARIA نیاز ندارند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : کاربر نمی‌تواند مقدار عنصر را تغییر دهد.
- `"false"`
  - : کاربر می‌تواند مقدار عنصر را تنظیم کند.

## مثال‌ها

در این مثال، ویژگی `aria-readonly` روی عنصری با شناسه `txtBoxInput` برابر با «true» قرار داده شده است که نشان می‌دهد این ورودی در حال حاضر فقط‌خواندنی است. با استفاده از `ariaReadOnly` مقدار آن را به «false» تغییر می‌دهیم.

```html
<div id="txtboxMultilineLabel">برچسب‌های مقاله را وارد کنید</div>
<div
  role="textbox"
  id="txtBoxInput"
  contenteditable="true"
  aria-multiline="true"
  aria-labelledby="txtboxMultilineLabel"
  aria-readonly="true"></div>
```

```js
let el = document.getElementById("txtBoxInput");
console.log(el.ariaReadOnly); // "true"
el.ariaReadOnly = "false";
console.log(el.ariaReadOnly); // "false"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش ARIA: textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)