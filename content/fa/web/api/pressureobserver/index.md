---
title: PressureObserver
slug: Web/API/PressureObserver
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PressureObserver
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

رابط **`PressureObserver`** بخشی از [Compute Pressure API](/en-US/docs/Web/API/Compute_Pressure_API) است و برای مشاهدهٔ تغییرات فشار منابع سیستمی مانند CPU به کار می‌رود.

## سازنده

- {{domxref("PressureObserver.PressureObserver","PressureObserver()")}} {{experimental_inline}}
  - : یک شیء `PressureObserver` جدید می‌سازد و آن را برمی‌گرداند.

## ویژگی‌های ایستا

- {{domxref("PressureObserver.knownSources_static", "PressureObserver.knownSources")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : آرایه‌ای از مقادیر {{domxref("PressureRecord.source","source")}} را برمی‌گرداند که توسط عامل کاربر پشتیبانی می‌شوند.

## متدهای نمونه

- {{domxref("PressureObserver.observe","PressureObserver.observe()")}} {{experimental_inline}}
  - : هنگامی که یک رکورد فشار برای `source` مشخص‌شده مشاهده شود، تابع callback مربوط به مشاهده‌گر فشار را فراخوانی می‌کند.
- {{domxref("PressureObserver.unobserve","PressureObserver.unobserve()")}} {{experimental_inline}}
  - : دریافت رکوردهای فشار از `source` مشخص‌شده را برای تابع callback مربوط به مشاهده‌گر فشار متوقف می‌کند.
- {{domxref("PressureObserver.disconnect","PressureObserver.disconnect()")}} {{experimental_inline}}
  - : دریافت رکوردهای فشار از همهٔ منابع را برای تابع callback مربوط به مشاهده‌گر فشار متوقف می‌کند.
- {{domxref("PressureObserver.takeRecords","PressureObserver.takeRecords()")}} {{experimental_inline}}
  - : فهرست کنونی رکوردهای فشار ذخیره‌شده در مشاهده‌گر فشار را برمی‌گرداند و آن را خالی می‌کند.

## نمونه‌ها

### ثبت فشار کنونی

این مثال یک `PressureObserver` می‌سازد و هرگاه تغییری در فشار رخ دهد اقدامی انجام می‌دهد. بازهٔ نمونه‌برداری روی ۱۰۰۰ میلی‌ثانیه تنظیم شده است؛ یعنی حداکثر هر ثانیه یک بار به‌روزرسانی دریافت می‌شود.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(`Current pressure ${lastRecord.state}`);
  if (lastRecord.state === "critical") {
    // disable video feeds
  } else if (lastRecord.state === "serious") {
    // disable video filter effects
  } else {
    // enable all video feeds and filter effects
  }
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

## همچنین ببینید

- {{domxref('PerformanceObserver')}}
- {{domxref('MutationObserver')}}
- {{domxref('ResizeObserver')}}
- {{domxref('IntersectionObserver')}}