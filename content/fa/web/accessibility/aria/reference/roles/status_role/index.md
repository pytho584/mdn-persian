---
title: "ARIA: status role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: status role"
short-title: status
slug: Web/Accessibility/ARIA/Reference/Roles/status_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#status
sidebar: accessibilitysidebar
---

نقش `status` یک [منطقه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) را تعریف می‌کند که حاوی اطلاعات راهنمایی برای کاربر است و به اندازه‌ای مهم نیست که یک [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) باشد.

## توضیحات

یک `status` نوعی [منطقه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) است که اطلاعات راهنمایی ارائه می‌دهد که به اندازه‌ای مهم نیست که یک هشدار (alert) را توجیه کند، زیرا هشدار بلافاصله اعلام فعالیت فعلی کاربر را قطع می‌کند. این معمولاً، اما نه لزوماً، به صورت یک نوار وضعیت نمایش داده می‌شود.

هنگامی که محتوای status به‌روزرسانی می‌شود، به آن فوکوس ندهید. مناطق زنده برای اطلاع‌رسانی به کاربران در مورد به‌روزرسانی‌های پویایی که در سایر مناطق صفحه وب فعلی رخ داده‌اند، در نظر گرفته شده‌اند، اما نیازی به قطع فعالیت فعلی کاربر با تغییر زمینه ندارند. اگر موقعیتی نیاز به جابجایی فوکوس دارد، استفاده از یک `status` یا سایر مناطق زنده احتمالاً مناسب نیست.

عناصر با نقش status دارای یک [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) ضمنی با مقدار `polite` و یک [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) ضمنی با مقدار `true` هستند.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic)
  - : تعریف می‌کند که آیا فناوری‌های کمکی باید تمام یا فقط بخشی از منطقه تغییر یافته را ارائه دهند. عناصر با نقش `status` دارای یک `aria-atomic` ضمنی با مقدار `true` هستند.

- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
  - : تعریف می‌کند که چه زمانی فناوری کمکی باید کاربر را از به‌روزرسانی‌های محتوا مطلع کند. عناصر با نقش `status` دارای یک `aria-live` ضمنی با مقدار `polite` هستند، به این معنی که صفحه‌خوان‌ها تغییرات داخل log را زمانی که کاربر بیکار است اعلام می‌کنند.

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : برخی از صفحه‌خوان‌ها نام یک عنصر status را قبل از اعلام محتوای آن اعلام می‌کنند. اگر یک نام قابل مشاهده است، با استفاده از `aria-labelledby` به آن ارجاع دهید. گنجاندن یک `aria-label` روشی برای مقدمه‌سازی محتوای قابل مشاهده یک عنصر status با متنی که هنگام خواندن محتوا توسط صفحه‌خوان نمایش داده نمی‌شود، فراهم می‌کند. نام‌گذاری یک status الزامی نیست، بنابراین اگر هیچ چیز مناسبی وجود ندارد، می‌توان هر دو ویژگی را حذف کرد.

## Specifications

{{Specifications}}

## همچنین ببینید

- [ARIA: نقش `alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [ARIA: نقش `log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)
- [ARIA: نقش `marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)
- [ARIA: نقش `timer`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role)
- [مناطق زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)