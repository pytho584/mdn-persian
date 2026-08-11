---
title: "fetchpriority HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/fetchpriority"
translated_by: "n8n + AI"
---

**`fetchpriority`** یک attribute در HTML است که به توسعه‌دهنده اجازه می‌دهد مشخص کند دریافت یک تصویر خاص در مراحل اولیه بارگذاری صفحه، تأثیر بیشتری یا کمتری روی تجربه کاربری دارد نسبت به چیزی که مرورگر به‌طور معمول می‌تواند هنگام تعیین اولویت داخلی حدس بزند. این کار به مرورگر امکان می‌دهد اولویت را افزایش یا کاهش دهد و احتمالاً تصویر را زودتر یا دیرتر از حالت عادی بارگذاری کند.

این attribute روی المان‌های {{HTMLElement("img")}}، {{HTMLElement("link")}} و {{HTMLElement("script")}} قابل استفاده است. همچنین یک [معادل SVG](/en-US/docs/Web/SVG/Reference/Attribute/fetchpriority) هم دارد.

از اولویت fetch می‌توان برای تکمیل [preload](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) استفاده کرد. به این صورت که توسعه‌دهنده می‌تواند اولویت یک منبع را نسبت به منابع کم‌اهمیت‌تری که اولویت پیش‌فرض بالاتری دارند، افزایش دهد. مثلاً اگر توسعه‌دهنده بداند یک تصویر خاص تأثیر زیادی روی {{glossary("Largest Contentful Paint")}} (LCP) سایت دارد، می‌تواند [`<link rel="preload">`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) را برای آن تصویر اضافه کند و سپس با استفاده از attribute `fetchpriority` اولویت را بیشتر بالا ببرد.

توجه داشته باشید که هم اولویت داخلی هر عملیات fetch و هم تأثیر `fetchpriority` روی اولویت، کاملاً به مرورگر بستگی دارد.

این attribute از نوع [enumerated](/en-US/docs/Glossary/Enumerated) است و می‌تواند یکی از مقادیر زیر را داشته باشد:

- `high`
  - : منبع خارجی با اولویت بالا نسبت به سایر منابع خارجی دریافت می‌شود.
- `low`
  - : منبع خارجی با اولویت پایین نسبت به سایر منابع خارجی دریافت می‌شود.
- `auto`
  - : ترجیحی برای اولویت fetch تعیین نمی‌کند. اگر مقداری تنظیم نشود یا مقدار نامعتبر باشد از این مقدار استفاده می‌شود. این مقدار پیش‌فرض است.

## نکات استفاده

این attribute باید به‌ندرت استفاده شود، زیرا اولویت‌بندی بیش از حد یا نادرست می‌تواند عملکرد را کاهش دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- SVG {{svgattr("fetchpriority")}} attribute