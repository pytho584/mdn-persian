---
title: "PerformancePaintTiming: paintTime property"
short-title: paintTime
slug: Web/API/PerformancePaintTiming/paintTime
page-type: web-api-instance-property
browser-compat: api.PerformancePaintTiming.paintTime
---

{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`paintTime`** از رابط {{domxref("PerformancePaintTiming")}}، {{domxref("DOMHighResTimeStamp","زمان‌سنج")}} مربوط به پایان مرحله‌ی رندرینگ و آغاز مرحله‌ی paint (نقاشی) را برمی‌گرداند.

مقدار `paintTime` در مرورگرهای مختلف سازگار است: مقدار آن باید در پیاده‌سازی‌های مختلف یکسان باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

به [دریافت زمان‌بندی‌های جداگانه‌ی paint و presentation](/en-US/docs/Web/API/PerformancePaintTiming#getting_separate_paint_and_presentation_timings) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformancePaintTiming.presentationTime")}}