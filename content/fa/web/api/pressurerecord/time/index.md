---
title: "PressureRecord: time property"
---

---
title: "PressureRecord: time property"
short-title: time
slug: Web/API/PressureRecord/time
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PressureRecord.time
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

ویژگی **`time`** فقط‌خواندنی، {{domxref("DOMHighResTimeStamp","timestamp", "", "no-code")}} ثبت‌شده برای یک {{domxref("PressureRecord")}} را بازمی‌گرداند. این ویژگی با زمانی مطابقت دارد که داده از سیستم، نسبت به [مبدأ زمانی شیء سراسری](/en-US/docs/Web/API/Performance/timeOrigin) که در آن {{domxref("PressureObserver")}} اعلان را تولید کرده است، به دست آمده است.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که زمان ایجاد {{domxref("PressureRecord")}} را نشان می‌دهد.

## مثال‌ها

### استفاده از ویژگی `time`

در مثال زیر، مقدار ویژگی `time` را در تابع بازخورد ناظر فشار (pressure observer) ثبت می‌کنیم.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(`Current pressure ${lastRecord.state}`);
  console.log(`Current pressure observed at ${lastRecord.time}`);
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