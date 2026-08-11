---
title: "<dir> HTML directory element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dir"
translated_by: "n8n + AI"
---

# عنصر `<dir>` (دایرکتوری) در HTML

عنصر **`<dir>`** یک [HTML](/en-US/docs/Web/HTML) منسوخ‌شده است که برای نگهداری فهرست دایرکتوری‌ها و فایل‌ها به کار می‌رفت. کاربر عامل (user agent) می‌توانست سبک‌ها و آیکون‌های خاصی را روی آن اعمال کند. از این عنصر قدیمی استفاده نکنید؛ به جای آن برای فهرست‌ها (از جمله فهرست فایل‌ها) از عنصر `<ul>` استفاده کنید.

> **هشدار:** این عنصر را به کار نبرید. اگرچه در نسخه‌های اولیه HTML وجود داشت، اما در HTML 4 منسوخ اعلام شد و بعداً به طور کامل حذف گردید.

## رابط DOM

این عنصر رابط `HTMLDirectoryElement` را پیاده‌سازی می‌کند.

## ویژگی‌ها (Attributes)

مانند تمام عناصر HTML دیگر، این عنصر از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `compact` {{Deprecated_Inline}} {{non-standard_inline}}
  - : این ویژگی Boolean (بولی) نشان می‌دهد که فهرست باید به صورت فشرده (compact) نمایش داده شود. تفسیر این ویژگی به کاربر عامل بستگی دارد و در همه مرورگرها کار نمی‌کند.

<!-- ## خلاصه فنی -->

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- سایر عناصر HTML مرتبط با فهرست: `<ol>`، `<ul>`، `<li>` و `<menu>`
- ویژگی‌های CSS که ممکن است برای سبک‌دهی به عنصر `<dir>` مفید باشند:
  - ویژگی `list-style` برای انتخاب نحوه نمایش شمارنده‌ها
  - [شمارنده‌های CSS (CSS counters)](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) برای مدیریت فهرست‌های تو در تو
  - ویژگی `line-height` برای شبیه‌سازی ویژگی منسوخ `compact`
  - ویژگی `margin` برای کنترل تورفتگی فهرست