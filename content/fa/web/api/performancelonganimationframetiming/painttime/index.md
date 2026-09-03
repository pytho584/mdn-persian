---
title: "PerformanceLongAnimationFrameTiming: paintTime property"
short-title: paintTime
slug: Web/API/PerformanceLongAnimationFrameTiming/paintTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.paintTime
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`paintTime`** در رابط {{domxref("PerformanceLongAnimationFrameTiming")}}، {{domxref("DOMHighResTimeStamp","timestamp")}} زمانی را برمی‌گرداند که فاز رندر پایان یافته و فریم انیمیشن شروع شده است.

`paintTime` به‌طور گسترده‌ای سازگار است: مقدار آن باید در پیاده‌سازی‌های مختلف یکسان باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## نمونه‌ها

برای نمونه‌های مربوط به API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceLongAnimationFrameTiming.presentationTime")}}