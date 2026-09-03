---
title: "PerformanceScriptTiming: windowAttribution property"
---

---
title: "PerformanceScriptTiming: windowAttribution property"
short-title: windowAttribution
slug: Web/API/PerformanceScriptTiming/windowAttribution
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.windowAttribution
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خصوصیت فقطخواندنی **`windowAttribution`** در رابط {{domxref("PerformanceScriptTiming")}} یک مقدار شمارشی (enumerated) برمی‌گرداند که رابطهٔ ظرف (container) را توصیف می‌کند — خواه سند سطح بالا (top-level document) باشد، خواه یک {{htmlelement("iframe")}} — که اسکریپتِ عاملِ فریم انیمیشن طولانی (LoAF) در آن اجرا شده است، نسبت به پنجره‌ای که سند جاری را اجرا می‌کند.

## مقدار

یک مقدار شمارشی که می‌تواند یکی از موارد زیر باشد:

- `"ancestor"`
  - : سندِ جاری از نوادگان (descendant) سندی است که اسکریپت در آن اجرا شده است؛ یعنی سند جاری درون همان سند و داخل یک `<iframe>` جاسازی شده است.
- `"descendant"`
  - : اسکریپت در سندی از نوادگان (descendant) اجرا شده است که درون سند جاری و داخل یک `<iframe>` جاسازی شده است.
- `"other"`
  - : مکان سندی که اسکریپت در آن اجرا شده است قابل تعیین نبود.
- `"same-page"`
  - : اسکریپت در نسخه‌ای از سند جاری اجرا شده است که درون خودِ سند جاری و در یک `<iframe>` جاسازی شده است.
- `"self"`
  - : اسکریپت در سند جاری اجرا شده است.

## مثال‌ها

برای نمونه‌های مرتبط با Long Animation Frames API، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}