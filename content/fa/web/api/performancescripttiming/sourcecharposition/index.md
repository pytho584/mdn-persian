---
title: "PerformanceScriptTiming: sourceCharPosition property"
short-title: sourceCharPosition
slug: Web/API/PerformanceScriptTiming/sourceCharPosition
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.sourceCharPosition
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`sourceCharPosition`** از رابط {{domxref("PerformanceScriptTiming")}} یک عدد را برمی‌گرداند که موقعیت نویسهٔ اسکریپتِ ویژگی اسکریپتی را نشان می‌دهد که در فریم انیمیشن طولانی (LoAF) نقش داشته است.

توجه به این نکته مهم است که مکان گزارش‌شدهٔ تابع، «نقطهٔ ورود» اسکریپت خواهد بود؛ یعنی سطح بالای پشته، نه هر تابع فرعی کند خاص. برای بحث بیشتر در این مورد، {{domxref("PerformanceScriptTiming.sourceFunctionName")}} را ببینید.

## مقدار

یک عدد. اگر موقعیت نویسهٔ اسکریپت پیدا نشود، `-1-` برمی‌گرداند.

## مثال‌ها

برای مثال‌های مرتبط با API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}