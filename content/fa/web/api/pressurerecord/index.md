---
title: PressureRecord
slug: Web/API/PressureRecord
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PressureRecord
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

رابط **`PressureRecord`** بخشی از [Compute Pressure API](/en-US/docs/Web/API/Compute_Pressure_API) است و روند فشار یک منبع را در یک لحظهٔ خاص از گذار توصیف می‌کند.

## ویژگی‌های نمونه

- {{domxref("PressureRecord.source")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک رشته که منبعِ مبدأِ این رکورد را مشخص می‌کند.
- {{domxref("PressureRecord.state")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک رشته که وضعیت فشارِ ثبت‌شده را مشخص می‌کند.
- {{domxref("PressureRecord.time")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان (timestamp) این رکورد را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("PressureRecord.toJSON()")}} {{experimental_inline}}
  - : یک نمایش JSON از شیء `PressureRecord` برمی‌گرداند.

## مثال‌ها

### استفاده از شیء `PressureRecord`

در مثال زیر، ویژگی‌های شیء `PressureRecord` را در تابع callback ناظر فشار ثبت (log) می‌کنیم.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(`Current pressure is ${lastRecord.state}`);
  console.log(`Current pressure observed at ${lastRecord.time}`);
  console.log(`Current pressure source: ${lastRecord.source}`);
}

try {
  const observer = new PressureObserver(callback);
  await observer.observe("cpu", {
    sampleInterval: 1000, // 1000ms
  });
} catch (error) {
  // report error setting up the observer
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}