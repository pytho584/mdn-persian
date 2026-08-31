---
title: "ARIA: aria-braillelabel attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-braillelabel attribute"
short-title: aria-braillelabel
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-braillelabel
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-braillelabel` یک مقدار رشتهای تعریف میکند که عنصر فعلی را برچسبگذاری میکند و قرار است به بریل تبدیل شود.

## توضیحات

ویژگی سراسری `aria-braillelabel` مشابه ویژگی سراسری [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) است، از این جهت که یک مقدار رشتهای تعریف میکند که عنصر فعلی را برچسبگذاری میکند. در حالی که `aria-label` توسط صفحهخوان خوانده میشود، محتویات ویژگی `aria-braillelabel` به بریل تبدیل میشوند و نام قابل تشخیصی از شیء را در بریل در اختیار کاربر قرار میدهند.

هدف ویژگی `aria-braillelabel` بازنویسی روش بومیسازی و بیان نام دسترسپذیر یک عنصر در بریل توسط فناوریهای کمکی است. فقط زمانی باید استفاده شود که بدون این ویژگی، نام دسترسپذیر هنگام تبدیل به بریل، تجربه کاربری مطلوبی ایجاد نکند.

هنگام استفاده از `aria-braillelabel` اطمینان حاصل کنید که:

- عنصری که `aria-braillelabel` روی آن اعمال شده است، نام دسترسپذیر معتبری دارد.
- مقدار `aria-braillelabel` دارای محتوای واقعی است و خالی یا فقط شامل فاصله (whitespace) در یونیکد یا بریل یونیکد نیست.
- مقدار با نام دسترسپذیر یکسان نیست.
- مقادیر `aria-braillelabel` بومیسازی شده‌اند تا با زبان سند هماهنگ باشند.
- به کاربر اطلاع دهید که این ویژگی در دسترس است، به‌ویژه اگر محتوا شامل الگوهای بریل یونیکد است، تا کاربر بداند تنظیمات را برای اعمال ترجمه‌های بریل ویژه کاربر تنظیم کند.

> [!NOTE]
> فناوری‌های کمکی که از بریل پشتیبانی می‌کنند می‌توانند نام‌های دسترس‌پذیر را به بریل تبدیل کنند.
> بنابراین، فقط زمانی از `aria-braillelabel` استفاده کنید که نام دسترس‌پذیر تجربه کاربری مورد نظر شما نباشد.

استفاده تنها از نام دسترس‌پذیر، مثلاً از محتوا یا از طریق `aria-label`، تقریباً همیشه تجربه کاربری بهتری است؛ بنابراین برای تکرار `aria-label` از `aria-braillelabel` استفاده نکنید. فقط زمانی از `aria-braillelabel` استفاده کنید که نام دسترس‌پذیر نتواند نمایش بریل مناسبی فراهم کند.

```html
<button aria-braillelabel="***">
  <img alt="3 out of 5 stars" src="three_stars.png" />
</button>
```

یک نمایشگر بریل ممکن است "btn \*\*\*" را در بریل نمایش دهد، نه عبارت طولانی‌تر "btn gra 3 out of 5 stars" را.

## مقادیر

- `<string>`
  - : مقدار یک رشته است، یک نوع مقدار بدون محدودیت، که قرار است به بریل تبدیل شود.

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- {{domxref("Element.ariaBrailleLabel")}}
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
- [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription)