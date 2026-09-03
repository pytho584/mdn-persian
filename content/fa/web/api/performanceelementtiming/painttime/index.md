---
title: "PerformanceElementTiming: paintTime property"
short-title: paintTime
slug: Web/API/PerformanceElementTiming/paintTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.paintTime
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`paintTime`** در رابط {{domxref("PerformanceElementTiming")}}، یک {{domxref("DOMHighResTimeStamp","timestamp")}} برمی‌گرداند که نشان‌دهندهٔ پایان مرحلهٔ رندر و آغاز شدن مرحلهٔ paint است.

`paintTime` تا حد زیادی بین پیاده‌سازی‌های مختلف سازگار است؛ یعنی مقدار آن باید در پیاده‌سازی‌های مختلف یکسان باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

مطالعهٔ [مشاهدهٔ زمان‌بندی‌های جداگانهٔ paint و presentation](/en-US/docs/Web/API/PerformanceElementTiming#observing_separate_paint_and_presentation_timings).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceElementTiming.presentationTime")}}