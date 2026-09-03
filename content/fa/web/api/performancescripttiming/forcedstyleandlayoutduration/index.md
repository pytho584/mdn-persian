---
title: "PerformanceScriptTiming: forcedStyleAndLayoutDuration property"
short-title: forcedStyleAndLayoutDuration
slug: Web/API/PerformanceScriptTiming/forcedStyleAndLayoutDuration
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceScriptTiming.forcedStyleAndLayoutDuration
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`forcedStyleAndLayoutDuration`** از رابط {{domxref("PerformanceScriptTiming")}} یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که نشان‌دهندهٔ کل زمان صرف‌شده (به میلی‌ثانیه) توسط اسکریپت برای پردازش چیدمان/سبک اجباری است. برای درک اینکه چه چیزی موجب این وضعیت می‌شود، به مقالهٔ [پرهیز از نوسازی چیدمان (layout thrashing)](https://web.dev/articles/avoid-large-complex-layouts-and-layout-thrashing#avoid_layout_thrashing) مراجعه کنید.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## نمونه‌ها

برای نمونه‌های مرتبط با API فریم‌های انیمیشن طولانی، بخش [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}