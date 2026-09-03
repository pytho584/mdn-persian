---
title: "PerformancePaintTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformancePaintTiming/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformancePaintTiming.toJSON
---

{{APIRef("Performance API")}}

متد **`toJSON()`** در رابط {{domxref("PerformancePaintTiming")}} یک {{Glossary("Serialization","سریالساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PerformancePaintTiming")}} برمیگرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریالسازی شدهی شیء {{domxref("PerformancePaintTiming")}} است.

## مثالها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformancePaintTiming` برمیگرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "paint", buffered: true });
```

این کار یک شیء JSON مانند زیر را ثبت (log) میکند:

```json
{
  "name": "first-contentful-paint",
  "entryType": "paint",
  "startTime": 234.5,
  "duration": 0
}
```

برای دریافت یک رشته JSON، میتوانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این تابع به صورت خودکار `toJSON()` را فراخوانی میکند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}