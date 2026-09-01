---
title: "Element: ariaPlaceholder property"
short-title: ariaPlaceholder
slug: Web/API/Element/ariaPlaceholder
page-type: web-api-instance-property
browser-compat: api.Element.ariaPlaceholder
---

{{APIRef("DOM")}}

ویژگی **`ariaPlaceholder`** در رابط {{domxref("Element")}} منعکس‌کننده مقدار ویژگی `aria-placeholder` است که یک راهنمای کوتاه برای کمک به کاربر در هنگام ورود داده زمانی که کنترل مقداری ندارد، تعریف می‌کند.

> [!NOTE]
> در صورت امکان از عنصر HTML {{htmlelement("input")}} با `type="text"` یا {{htmlelement("textarea")}} استفاده کنید، زیرا این عناصر دارای معناشناسی داخلی هستند و به ویژگی‌های ARIA نیاز ندارند.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، ویژگی `aria-placeholder` روی عنصری با شناسه `txtBoxInput` به یک رشته تنظیم شده است. با استفاده از `ariaPlaceholder` مقدار رشته را به مقدار دیگری به‌روزرسانی می‌کنیم.

```html
<div id="txtboxLabel">Enter your five-digit zip code</div>
<div
  role="textbox"
  id="txtBoxInput"
  contenteditable="true"
  aria-placeholder="5-digit zip code"
  aria-labelledby="txtboxLabel"></div>
```

```js
let el = document.getElementById("txtBoxInput");
console.log(el.ariaPlaceholder); // "5-digit zip code"
el.ariaPlaceholder = "12345";
console.log(el.ariaPlaceholder); // "12345"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)