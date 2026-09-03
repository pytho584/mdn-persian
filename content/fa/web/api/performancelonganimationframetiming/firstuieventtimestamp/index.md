---
title: "PerformanceLongAnimationFrameTiming: firstUIEventTimestamp property"
short-title: firstUIEventTimestamp
slug: Web/API/PerformanceLongAnimationFrameTiming/firstUIEventTimestamp
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.firstUIEventTimestamp
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`firstUIEventTimestamp`** از رابط {{domxref("PerformanceLongAnimationFrameTiming")}} یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان اولین رویداد UI (مانند رویداد ماوس یا صفحه‌کلید) را که در طول فریم انیمیشن جاری پردازش شده است، نشان می‌دهد. توجه داشته باشید که این برچسب زمانی می‌تواند قبل از شروع این فریم انیمیشن باشد اگر بین وقوع رویداد و پردازش آن تأخیری وجود داشته باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceScriptTiming")}}