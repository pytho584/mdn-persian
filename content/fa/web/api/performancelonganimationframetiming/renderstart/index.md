---
title: "PerformanceLongAnimationFrameTiming: renderStart property"
short-title: renderStart
slug: Web/API/PerformanceLongAnimationFrameTiming/renderStart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.renderStart
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`renderStart`** از رابط {{domxref("PerformanceLongAnimationFrameTiming")}}، یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان شروع چرخهٔ رندر را نشان می‌دهد. این چرخه شامل فراخوانی‌های {{domxref("Window.requestAnimationFrame()")}}، محاسبهٔ استایل و چیدمان (layout)، فراخوانی‌های {{domxref("ResizeObserver")}} و فراخوانی‌های {{domxref("IntersectionObserver")}} است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

برای مثال‌های مربوط به Long Animation Frames API، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceScriptTiming")}}
