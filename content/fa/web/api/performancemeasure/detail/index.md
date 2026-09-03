---
title: "PerformanceMeasure: detail property"
---

---
title: "PerformanceMeasure: detail property"
short-title: detail
slug: Web/API/PerformanceMeasure/detail
page-type: web-api-instance-property
browser-compat: api.PerformanceMeasure.detail
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`detail`** فراداده‌ی دلخواهی را برمی‌گرداند که هنگام ساخت نشان (mark) در آن گنجانده شده است (زمانی که از {{domxref("Performance.measure","performance.measure()")}} استفاده می‌کنید).

## Value

مقداری را برمی‌گرداند که روی آن تنظیم شده است (از `markOptions` مربوط به {{domxref("Performance.measure","performance.measure()")}}).

## Examples

مثال زیر ویژگی `detail` را نشان می‌دهد.

```js
performance.measure("dog", { detail: "labrador", start: 0, end: 12345 });

const dogEntries = performance.getEntriesByName("dog");

dogEntries[0].detail; // labrador
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```