---
title: "PressureObserver: PressureObserver() constructor"
---

---
title: "PressureObserver: PressureObserver() constructor"
short-title: PressureObserver()
slug: Web/API/PressureObserver/PressureObserver
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.PressureObserver.PressureObserver
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

سازنده‌ی **`PressureObserver()`** یک شیء جدید {{domxref("PressureObserver")}} می‌سازد که برای مشاهده‌ی تغییرات فشار منابع سیستمی مانند CPU به کار می‌رود.

## سینتکس

```js-nolint
new PressureObserver(callback)
```

### پارامترها

- `callback`
  - : تابع بازخوردی که هنگام مشاهده شدن رکوردهای فشار فراخوانی می‌شود. هنگام فراخوانی این تابع، پارامترهای زیر در دسترس هستند:
    - `changes`
      - : آرایه‌ای شامل تمام اشیاء {{domxref("PressureRecord")}} که از آخرین بار فراخوانی تابع بازخورد، یا آخرین باری که متد {{domxref("PressureObserver.takeRecords", "takeRecords()")}} مشاهده‌گر فراخوانی شده است، ثبت شده‌اند.
    - `observer`
      - : شیء {{domxref("PressureObserver","observer")}} که رکوردهای بالا را دریافت می‌کند.

### مقدار بازگشتی

یک شیء جدید {{domxref("PressureObserver")}} به‌همراه تابع `callback` مشخص‌شده برگردانده می‌شود. این تابع، زمانی که متد {{domxref("PressureObserver.observe()")}} برای مشاهده تغییرات فشار فراخوانی شده باشد، صدا زده خواهد شد.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر [Compute Pressure API](/en-US/docs/Web/API/Compute_Pressure_API) به‌واسطه یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) از نوع {{httpheader('Permissions-Policy/compute-pressure','compute-pressure')}} مجاز شناخته نشود، پرتاب می‌شود.

## مثال‌ها

### ثبت فشار فعلی

در این مثال یک {{domxref("PressureObserver")}} ساخته می‌شود و هر زمان که تغییری در فشار رخ دهد، اقدام لازم انجام می‌گیرد. بازه نمونه‌برداری روی ۱۰۰۰ میلی‌ثانیه تنظیم شده است؛ یعنی حداکثر هر ثانیه یک‌بار به‌روزرسانی انجام می‌شود.

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