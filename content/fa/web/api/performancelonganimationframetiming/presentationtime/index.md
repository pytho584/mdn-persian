---
title: "PerformanceLongAnimationFrameTiming: presentationTime property"
short-title: presentationTime
slug: Web/API/PerformanceLongAnimationFrameTiming/presentationTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming.presentationTime
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`presentationTime`** از رابط {{domxref("PerformanceLongAnimationFrameTiming")}}، {{domxref("DOMHighResTimeStamp","زمان‌مهر")}}ای را بازمی‌گرداند که نشان‌دهنده‌ی لحظه‌ای است که به‌روزرسانی رابط کاربری واقعاً روی صفحه نمایش داده شده است.

`presentationTime` اختیاری است – ممکن است برخی مرورگرها همواره مقدار `0` برگردانند یا اصلاً این مقدار را در معرض دید قرار ندهند. مقدار آن همچنین وابسته به پیاده‌سازی است – ممکن است در مرورگرهای مختلفی که آن را در معرض دید قرار می‌دهند متفاوت باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} یا {{jsxref("null")}} اگر مقدار در معرض دید قرار نگرفته باشد.

## مثال‌ها

برای نمونه‌های مرتبط با رابط برنامه‌نویسی فریم‌های انیمیشن طولانی (Long Animation Frames API)، به [زمان‌بندی فریم‌های انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceLongAnimationFrameTiming.paintTime")}}