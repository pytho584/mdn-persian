```
---
title: "LargestContentfulPaint: presentationTime property"
short-title: presentationTime
slug: Web/API/LargestContentfulPaint/presentationTime
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.presentationTime
---

{{APIRef("Performance API")}}

خاصیت فقط-خواندنی **`presentationTime`** از رابط {{domxref("LargestContentfulPaint")}}، {{domxref("DOMHighResTimeStamp","timestamp")}} (زمان‌سنج) را برمی‌گرداند که نشان‌دهندهٔ زمانی است که پیکسل‌های نقاشی‌شده واقعاً روی صفحه نمایش داده شده‌اند.

`presentationTime` اختیاری است — برخی مرورگرها ممکن است همیشه `0` برگردانند یا اصلاً این مقدار را ارائه ندهند. مقدار آن همچنین به پیاده‌سازی وابسته است — ممکن است در مرورگرهای مختلفی که آن را ارائه می‌دهند متفاوت باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} یا {{jsxref("null")}} اگر مقدار ارائه نشده باشد.

## مثال‌ها

به [مشاهدهٔ زمان‌بندی‌های جداگانهٔ paint و presentation](/en-US/docs/Web/API/LargestContentfulPaint#observing_separate_paint_and_presentation_timings) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LargestContentfulPaint.paintTime")}}
```