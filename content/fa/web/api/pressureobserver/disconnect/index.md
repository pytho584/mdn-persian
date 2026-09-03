---
title: "PressureObserver: disconnect() method"
short-title: disconnect()
slug: Web/API/PressureObserver/disconnect
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PressureObserver.disconnect
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

متد **`disconnect()`** در رابط {{domxref('PressureObserver')}}، فراخوان (callback) ناظر فشار را از دریافت رکوردهای فشار از همهٔ منابع متوقف می‌کند.

## نحو (Syntax)

```js-nolint
disconnect()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### توقف یک ناظر فشار

مثال زیر ۲۰ نمونه جمع‌آوری می‌کند و سپس ناظر فشار را قطع می‌کند تا دریافت رکوردهای فشار بیشتر غیرفعال شود.

```js
const samples = [];

function pressureChange(records, observer) {
  for (const record of records) {
    samples.push(record.state);
    // We only want 20 samples
    if (samples.length === 20) {
      observer.disconnect();
      return;
    }
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