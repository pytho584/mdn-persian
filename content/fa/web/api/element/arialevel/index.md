---
title: "Element: ariaLevel property"
short-title: ariaLevel
slug: Web/API/Element/ariaLevel
page-type: web-api-instance-property
browser-compat: api.Element.ariaLevel
---

{{APIRef("DOM")}}

ویژگی **`ariaLevel`** از رابط {{domxref("Element")}} نشان‌دهنده مقدار ویژگی `aria-level` است که سطح سلسله‌مراتبی یک عنصر را در یک ساختار تعریف می‌کند.

> [!NOTE]
> تا حد امکان از یک HTML {{htmlelement("Heading_Elements", "h1")}} یا سایر سطح‌های عنوان صحیح استفاده کنید، زیرا این‌ها معناشناسی داخلی دارند و به ویژگی‌های ARIA نیاز ندارند.

## مقدار

یک رشته شامل یک عدد صحیح.

## مثال‌ها

در این مثال، ویژگی `aria-level` روی عنصری با شناسه `main-heading` روی "1" تنظیم شده است. با استفاده از `ariaLevel` مقدار را به "2" به‌روز می‌کنیم.

```html
<div role="heading" id="main-heading" aria-level="1">
  This is a main page heading
</div>
```

```js
let el = document.getElementById("main-heading");
console.log(el.ariaLevel); // "1"
el.ariaLevel = "2";
console.log(el.ariaLevel); // "2"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نقش heading در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role)