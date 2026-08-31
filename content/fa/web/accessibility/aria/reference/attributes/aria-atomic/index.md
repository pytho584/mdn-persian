---
title: "ARIA: aria-atomic attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-atomic attribute"
short-title: aria-atomic
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-atomic
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-atomic
sidebar: accessibilitysidebar
---

در مناطق زنده ARIA، ویژگی سراسری `aria-atomic` نشان می‌دهد که آیا فناوری‌های کمکی مانند صفحه‌خوان، همه یا فقط بخش‌هایی از منطقه تغییر یافته را بر اساس اعلان‌های تغییر تعریف‌شده توسط ویژگی [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) ارائه خواهند کرد یا خیر.

مناطق زنده بخش‌هایی از یک صفحه وب هستند که چه با تعامل کاربر و چه بدون آن، زمانی که فوکوس کاربر در جای دیگری است، به‌روزرسانی می‌شوند. از آنجا که این به‌روزرسانی‌ها خارج از فوکوس کاربر رخ می‌دهند، فناوری‌های کمکی مانند صفحه‌خوان‌ها ممکن است به‌روزرسانی را برای گزارش به کاربر «نبینند». WAI-ARIA دارای ۴ ویژگی است که به توسعه‌دهنده امکان می‌دهد این مناطق زنده را شناسایی کرده و به فناوری کمکی بگوید چگونه آن‌ها را پردازش کند، از جمله [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)، [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant)، [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) و `aria-atomic`.

هنگامی که محتوای یک منطقه زنده تغییر می‌کند، DOM از عنصر تغییر یافته به سمت اجداد آن پیمایش می‌شود تا اولین عنصری که `aria-atomic` در آن تنظیم شده است پیدا شود. این تعیین می‌کند که چه محتوایی باید به کاربر ارائه شود.

اگر هیچ جدی به‌طور صریح `aria-atomic` را تنظیم نکرده باشد، فقط گره یا گره‌های محتوای منطقه زنده که به‌روزرسانی شده‌اند خوانده می‌شوند. تفاوت بین حذف کامل `aria-atomic` و تنظیم صریح گره جد یک منطقه زنده ARIA با `aria-atomic="false"` این است که تنظیم صریح `aria-atomic="false"` باعث می‌شود صفحه‌خوان از بالا رفتن در زنجیره اجداد متوقف شود. هر دو به خوانده شدن فقط گره به‌روزرسانی‌شده منجر می‌شوند. وقتی روی `aria-atomic="true"` تنظیم شود، کل منطقه تغییر یافته به‌صورت یکپارچه ارائه می‌شود، از جمله `label` گره به‌روزرسانی‌شده، در صورت وجود.

## مقادیر

- `false` (پیش‌فرض)
  - : فقط گره یا گره‌های تغییر یافته ارائه می‌شوند.
- `true`
  - : کل منطقه تغییر یافته به‌صورت یکپارچه ارائه می‌شود، از جمله برچسب تعریف‌شده توسط نویسنده در صورت وجود.

## نقش‌های مرتبط

استفاده شده در **همه** [نقش‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles).

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Event.ariaAtomic](/en-US/docs/Web/API/Element/ariaAtomic)