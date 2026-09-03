---
title: "PressureRecord: toJSON() method"
short-title: toJSON()
slug: Web/API/PressureRecord/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PressureRecord.toJSON
---

{{APIRef("Compute Pressure API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_service")}}{{securecontext_header}}

متد **`toJSON()`** یک {{Glossary("Serialization","serializer")}} است؛ یعنی نمایش JSON از شیء {{domxref("PressureRecord")}} را بازمی‌گرداند.

## سینتکس

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PressureRecord")}} است.

## مثال‌ها

### استفاده از متد `toJSON`

در این مثال، فراخوانی `lastRecord.toJSON()` یک نمایش JSON از شیء {{domxref("PressureRecord")}} برمی‌گرداند.

```js
function callback(records) {
  const lastRecord = records[records.length - 1];
  console.log(lastRecord.toJSON);
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

این کار یک شیء JSON مانند زیر را ثبت می‌کند:

```json
{
  "source": "cpu",
  "state": "fair",
  "time": 1712052746385.347
}
```

برای دریافت رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(lastRecord)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}