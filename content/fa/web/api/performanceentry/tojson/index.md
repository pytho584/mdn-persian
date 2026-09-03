---
title: "PerformanceEntry: toJSON() method"
---

---
title: "PerformanceEntry: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceEntry/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformanceEntry.toJSON
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`toJSON()`** یک {{Glossary("Serialization","سریالساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PerformanceEntry")}} برمیگرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریالسازی از شیء {{domxref("PerformanceEntry")}} است.

## مثالها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء {{domxref("PerformanceMark")}} برمیگرداند.

```js
performance.mark("debug-marker", {
  detail: "debugging-marker-123",
});

const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ entryTypes: ["mark"] });
```

این کار یک شیء JSON را مانند زیر ثبت میکند:

```json
{
  "name": "debug-marker",
  "entryType": "mark",
  "startTime": 158361,
  "duration": 0
}
```

توجه داشته باشید که این شیء شامل ویژگی {{domxref("PerformanceMark.detail", "detail")}} مربوط به `PerformanceMark` نیست.

برای دریافت یک رشته JSON، میتوانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد بهطور خودکار `toJSON()` را فراخوانی میکند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}