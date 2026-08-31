---
title: "ARIA: marquee role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: marquee role"
short-title: marquee
slug: Web/Accessibility/ARIA/Reference/Roles/marquee_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#marquee
sidebar: accessibilitysidebar
---

یک `marquee` نوعی [منطقه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) است که حاوی اطلاعات غیرضروری بوده و به‌طور مکرر تغییر می‌کند.

## توضیحات

نقش `marquee` یک منطقه را به‌عنوان نوعی ناحیه زنده تعریف می‌کند که اطلاعات غیرضروری را که به‌طور مکرر تغییر می‌کنند ارائه می‌دهد. نمونه‌هایی از marquee شامل تیکرهای سهام و بنرهای تبلیغاتی است؛ اطلاعاتی که لزوماً توسط کاربر جستجو نمی‌شوند و ممکن است به هر ترتیبی ارائه شوند. تفاوت اصلی بین `marquee` و [`log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role) این است که اطلاعات log به ترتیب معناداری مانند بر اساس تاریخ ارائه می‌شوند.

عناصر دارای نقش marquee مقدار ضمنی [aria-live](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) برابر با `off` دارند.

marquee باید یک نام قابل دسترس داشته باشد. اگر برچسب قابل مشاهده وجود دارد از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده کنید، در غیر این صورت از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
  - : تعیین می‌کند که فناوری کمکی چه زمانی باید کاربر را از به‌روزرسانی‌های محتوا مطلع کند. عناصر دارای نقش `marquee` مقدار ضمنی `aria-live` برابر با `off` دارند، به این معنی که صفحه‌خوان‌ها تغییرات داخل marquee را حتی زمانی که کاربر بیکار است اعلام نمی‌کنند.

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : `marquee` باید یک نام قابل دسترس داشته باشد. اگر برچسب قابل مشاهده وجود دارد از `aria-labelledby` استفاده کنید، در غیر این صورت از `aria-label` استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `alert` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [نقش `log` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)
- [نقش `status` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)
- [نقش `timer` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role)
- [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)