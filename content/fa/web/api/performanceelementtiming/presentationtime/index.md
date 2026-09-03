---
title: "PerformanceElementTiming: presentationTime property"
short-title: presentationTime
slug: Web/API/PerformanceElementTiming/presentationTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.presentationTime
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`presentationTime`** از رابط {{domxref("PerformanceElementTiming")}}، {{domxref("DOMHighResTimeStamp","timestamp")}} زمانی را برمی‌گرداند که عنصر واقعاً روی صفحه ترسیم شده است.

`presentationTime` اختیاری است — برخی مرورگرها ممکن است همیشه `0` برگردانند یا اصلاً مقدار را در معرض نمایش قرار ندهند. همچنین این مقدار وابسته به پیاده‌سازی است — ممکن است در میان مرورگرهایی که آن را در معرض نمایش قرار می‌دهند، متفاوت باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} یا {{jsxref("null")}} اگر مقدار در معرض نمایش قرار نگرفته باشد.

## مثال‌ها

مشاهده کنید: [مشاهده زمان‌بندی‌های جداگانه ترسیم و نمایش](/en-US/docs/Web/API/PerformanceElementTiming#observing_separate_paint_and_presentation_timings).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceElementTiming.paintTime")}}