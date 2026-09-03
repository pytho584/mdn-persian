---
title: "PerformancePaintTiming: presentationTime property"
short-title: presentationTime
slug: Web/API/PerformancePaintTiming/presentationTime
page-type: web-api-instance-property
browser-compat: api.PerformancePaintTiming.presentationTime
---

{{APIRef("Performance API")}}

**`presentationTime`** خاصیت فقطخواندنی رابط {{domxref("PerformancePaintTiming")}}، {{domxref("DOMHighResTimeStamp","timestamp")}} را هنگامی که پیکسلهای نقاشیشده واقعاً روی صفحه نمایش داده شدند، برمیگرداند.

`presentationTime` اختیاری است — برخی مرورگرها ممکن است همیشه `0` برگردانند یا اصلاً مقدار را در دسترس قرار ندهند. این مقدار همچنین به پیادهسازی وابسته است — ممکن است در مرورگرهایی که آن را در دسترس قرار میدهند متفاوت باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} یا {{jsxref("null")}} اگر مقدار در دسترس نباشد.

## مثالها

به [دریافت زمانبندیهای جداگانه paint و presentation](/en-US/docs/Web/API/PerformancePaintTiming#getting_separate_paint_and_presentation_timings) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformancePaintTiming.paintTime")}}