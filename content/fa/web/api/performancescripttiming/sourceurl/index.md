---
title: "PerformanceScriptTiming: sourceURL property"
short-title: sourceURL
slug: Web/API/PerformanceScriptTiming/sourceURL
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.sourceURL
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`sourceURL`** از رابط {{domxref("PerformanceScriptTiming")}} یک رشته را برمی‌گرداند که نشانی اینترنتی (URL) اسکریپت را نشان می‌دهد.

توجه به این نکته مهم است که مکان گزارش‌شدهٔ تابع، «نقطهٔ ورود» اسکریپت خواهد بود، یعنی بالاترین سطح پشته، نه هیچ زیرتابع کند خاصی. برای بحث بیشتر در این زمینه به {{domxref("PerformanceScriptTiming.sourceFunctionName")}} مراجعه کنید.

## مقدار

یک رشته. اگر نشانی اینترنتی پیدا نشود، یک رشتهٔ خالی برمی‌گرداند.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}