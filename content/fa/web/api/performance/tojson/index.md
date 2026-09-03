---
title: "Performance: toJSON() method"
short-title: toJSON()
slug: Web/API/Performance/toJSON
page-type: web-api-instance-method
browser-compat: api.Performance.toJSON
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`toJSON()`** از رابط {{domxref("Performance")}} یک {{Glossary("Serialization","serializer")}} است؛ این متد یک نمایش JSON از شیء {{domxref("Performance")}} برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازیِ شیء {{domxref("Performance")}} است.

JSON بازگشتی شامل ویژگی {{domxref("Performance.eventCounts", "eventCounts")}} نمی‌شود، زیرا از نوع {{domxref("EventCounts")}} است که عملیات `toJSON()` را ارائه نمی‌دهد.

> [!NOTE]
> شیء JSON شامل سریال‌سازیِ ویژگی‌های منسوخ‌شده {{domxref("performance.timing")}} و {{domxref("performance.navigation")}} است. برای دریافت نمایش JSON از رابط جدیدتر {{domxref("PerformanceNavigationTiming")}}، به‌جای آن از {{domxref("PerformanceNavigationTiming.toJSON()")}} استفاده کنید.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `performance.toJSON()` یک نمایش JSON از شیء `Performance` برمی‌گرداند.

```js
performance.toJSON();
```

این کار یک شیء JSON مانند زیر را لاگ می‌کند:

```json
{
  "timeOrigin": 1668077531367.4,
  "timing": {
    "connectStart": 1668077531372,
    "navigationStart": 1668077531367,
    "secureConnectionStart": 0,
    "fetchStart": 1668077531372,
    "domContentLoadedEventStart": 1668077531580,
    "responseStart": 1668077531372,
    "domInteractive": 1668077531524,
    "domainLookupEnd": 1668077531372,
    "responseEnd": 1668077531500,
    "redirectStart": 0,
    "requestStart": 1668077531372,
    "unloadEventEnd": 0,
    "unloadEventStart": 0,
    "domLoading": 1668077531512,
    "domComplete": 1668077531585,
    "domainLookupStart": 1668077531372,
    "loadEventStart": 1668077531585,
    "domContentLoadedEventEnd": 1668077531580,
    "loadEventEnd": 1668077531585,
    "redirectEnd": 0,
    "connectEnd": 1668077531372
  },
  "navigation": {
    "type": 0,
    "redirectCount": 0
  }
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(performance)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌صورت خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}