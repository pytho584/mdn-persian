---
title: "ARIA: log role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: log role"
short-title: log
slug: Web/Accessibility/ARIA/Reference/Roles/log_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#log
sidebar: accessibilitysidebar
---

نقش `log` برای شناسایی عنصری استفاده می‌شود که یک [منطقه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) ایجاد می‌کند که در آن اطلاعات جدید به ترتیب معنادار اضافه می‌شوند و اطلاعات قدیمی ممکن است حذف شوند.

## توضیحات

لاگ نوعی منطقه زنده است که در آن اطلاعات جدید به ترتیب معنادار اضافه می‌شوند و اطلاعات قدیمی ممکن است حذف شوند. نمونه‌ها شامل لاگ‌های گفتگو، تاریخچه پیام‌رسانی، لاگ بازی یا لاگ خطا هستند. برخلاف سایر مناطق زنده، در این نقش رابطه‌ای بین arrival آیتم‌های جدید در لاگ و ترتیب خواندن وجود دارد. لاگ شامل یک توالی معنادار است و اطلاعات جدید فقط به انتهای لاگ اضافه می‌شوند، نه در نقاط دلخواه.

برخلاف سایر انواع مناطق زنده، لاگ به صورت ترتیبی مرتب شده است و اطلاعات جدید فقط به انتهای لاگ اضافه می‌شوند. وقتی این نقش به یک عنصر اضافه می‌شود، مرورگر یک رویداد لاگ قابل دسترس به محصولات فناوری کمکی ارسال می‌کند که می‌توانند کاربر را در مورد آن مطلع کنند.

به طور پیش‌فرض، به‌روزرسانی‌ها فقط شامل تغییرات منطقه زنده هستند و زمانی که کاربر بیکار است اعلام می‌شوند. عناصر با نقش `log` مقدار ضمنی `aria-live` برابر با `polite` دارند. در جایی که کاربر نیاز دارد در هنگام تغییر کل منطقه زنده را بشنود، باید `aria-atomic="true"` تنظیم شود. برای اینکه اعلام‌ها در سریع‌ترین زمان ممکن انجام شوند و در جایی که ممکن است کاربر قطع شود، می‌توان `aria-live="assertive"` را برای به‌روزرسانی‌های تهاجمی‌تر تنظیم کرد.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic)
  - : تعیین می‌کند که آیا فناوری‌های کمکی باید همه یا فقط بخشی از منطقه تغییر یافته را ارائه دهند. عناصر با نقش `log` مقدار ضمنی `aria-atomic` برابر با `false` دارند.

- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
  - : تعیین می‌کند که فناوری کمکی چه زمانی باید کاربر را از به‌روزرسانی‌های محتوا مطلع کند. عناصر با نقش `log` مقدار ضمنی `aria-live` برابر با `polite` دارند، به این معنی که صفحه‌خوان‌ها تغییرات داخل لاگ را زمانی که کاربر بیکار است اعلام می‌کنند.

- `aria-label` و `aria-labelledby`
  - : `log` باید دارای نام قابل دسترس باشد. اگر برچسب قابل مشاهده‌ای وجود دارد از `aria-labelledby` استفاده کنید، در غیر این صورت از `aria-label` استفاده کنید.

## بهترین روش‌ها

برای ناحیه‌ای با متن اسکرول‌شونده، مانند تیکر سهام، باید از نقش [`marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role) استفاده شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ARIA: نقش `alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [ARIA: نقش `marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)
- [ARIA: نقش `status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)
- [ARIA: نقش `timer`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role)
- [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)