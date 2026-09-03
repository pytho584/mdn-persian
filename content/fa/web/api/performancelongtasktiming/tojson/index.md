---
title: "PerformanceLongTaskTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceLongTaskTiming/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PerformanceLongTaskTiming.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("PerformanceLongTaskTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PerformanceLongTaskTiming")}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PerformanceLongTaskTiming")}} است.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformanceLongTaskTiming` برمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "longtask", buffered: true });
```

این یک شیء JSON مانند زیر را ثبت می‌کند:

```json
{
  "name": "self",
  "entryType": "longtask",
  "startTime": 183,
  "duration": 60,
  "attribution": [
    {
      "name": "unknown",
      "entryType": "taskattribution",
      "startTime": 0,
      "duration": 0,
      "containerType": "window",
      "containerSrc": "",
      "containerId": "",
      "containerName": ""
    }
  ]
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}