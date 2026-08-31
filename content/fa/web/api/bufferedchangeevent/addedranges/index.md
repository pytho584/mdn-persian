---
title: "BufferedChangeEvent: addedRanges property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BufferedChangeEvent/addedRanges"
translated_by: "n8n + AI"
---

---
title: "BufferedChangeEvent: addedRanges property"
short-title: addedRanges
slug: Web/API/BufferedChangeEvent/addedRanges
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BufferedChangeEvent.addedRanges
---

{{APIRef("Media Source Extensions")}}{{AvailableInWorkers("window_and_dedicated")}}{{SeeCompatTable}}

**`addedRanges`** read-only property از رابط {{domxref("BufferedChangeEvent")}} یک شیء {{domxref("TimeRanges")}} برمی‌گرداند که محدوده‌های زمانی اضافه‌شده به {{domxref("ManagedSourceBuffer")}} مرتبط را نشان می‌دهد. این محدوده‌ها بین رویدادهای `updatestart` و `updateend` در آخرین اجرای الگوریتم پردازش فریم کدشده اضافه شده‌اند.

## Value

یک شیء {{domxref("TimeRanges")}}.

## Examples

برای مثالی از استفاده از `addedRanges`، به صفحه اصلی {{domxref("BufferedChangeEvent")}} مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("BufferedChangeEvent.removedRanges")}}
- {{domxref("ManagedSourceBuffer.bufferedchange_event", "bufferedchange")}} event
- {{domxref("ManagedSourceBuffer")}}
- {{domxref("TimeRanges")}}