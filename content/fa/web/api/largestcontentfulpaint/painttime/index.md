---
title: "LargestContentfulPaint: paintTime property"
---

---
title: "LargestContentfulPaint: paintTime property"
short-title: paintTime
slug: Web/API/LargestContentfulPaint/paintTime
page-type: web-api-instance-property
browser-compat: api.LargestContentfulPaint.paintTime
---

{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`paintTime`** از رابط {{domxref("LargestContentfulPaint")}}، {{domxref("DOMHighResTimeStamp","زمان‌مهر (timestamp)")}} مربوط به زمانی که فاز رندر (rendering) به پایان رسید و فاز نقاشی (paint) آغاز شد را برمی‌گرداند.

`paintTime` به طور گسترده‌ای قابل تعامل (interoperable) است: مقدار آن باید در پیاده‌سازی‌های مختلف یکسان باشد.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}}.

## مثال‌ها

به [مشاهده زمان‌بندی‌های مجزای نقاشی و ارائه](/en-US/docs/Web/API/LargestContentfulPaint#observing_separate_paint_and_presentation_timings) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("LargestContentfulPaint.presentationTime")}}