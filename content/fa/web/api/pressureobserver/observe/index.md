---
title: "PressureObserver: observe() method"
short-title: observe()
slug: Web/API/PressureObserver/observe
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PressureObserver.observe
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

متد **`observe()`** در رابط {{domxref("PressureObserver")}} به observer می‌گوید که نظارت بر تغییرات فشار را آغاز کند. پس از فراخوانی این متد، هر زمان که رکورد فشاری برای `source` مشخص‌شده مشاهده شود، observer تابع callback خود را صدا می‌زند.

هنگامی که یک {{domxref("PressureRecord")}} منطبق به دست آید، تابع callback مربوط به observer فشار فراخوانی می‌شود.

## نحو (Syntax)

```js-nolint
observe(source)
observe(source, options)
```

### پارامترها

- `source`
  - : رشته‌ای که مشخص می‌کند کدام {{domxref("PressureRecord.source", "source")}} باید مشاهده شود. فهرست منابع را در {{domxref("PressureRecord.source")}} و فهرست منابعی را که عامل کاربر (user agent) پشتیبانی می‌کند در {{domxref("PressureObserver.knownSources_static", "PressureObserver.knownSources")}} ببینید.
- `options` {{optional_inline}}
  - : شیئی برای پیکربندی مشاهده با ویژگی‌های زیر:
    - `sampleInterval` {{optional_inline}}
      - : عددی که بازه نمونه‌برداری درخواستی را بر حسب میلی‌ثانیه مشخص می‌کند. مقدار پیش‌فرض آن ۰ است؛ یعنی به‌روزرسانی‌ها با سریع‌ترین نرخی که سیستم بتواند مدیریت کند دریافت می‌شوند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} تکمیل (fulfill) می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که [Compute Pressure API](/en-US/docs/Web/API/Compute_Pressure_API) توسط {{httpheader('Permissions-Policy/compute-pressure','compute-pressure')}} [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مجاز نشده باشد.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که پارامتر `source` جزو منابع پشتیبانی‌شده توسط این عامل کاربر نباشد.

## مثال‌ها

### ثبت فشار فعلی

این مثال یک {{domxref("PressureObserver")}} می‌سازد و در هر بار تغییر فشار اقدام می‌کند. بازه نمونه‌برداری روی ۱۰۰۰ میلی‌ثانیه تنظیم شده است؛ یعنی حداکثر یک بار در هر ثانیه به‌روزرسانی انجام می‌شود.

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