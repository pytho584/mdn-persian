---
title: "PerformanceNavigationTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceNavigationTiming/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformanceNavigationTiming.toJSON
---

{{APIRef("Performance API")}}

متد **`toJSON()`** در رابط {{domxref("PerformanceNavigationTiming")}} یک {{Glossary("Serialization","serializer")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PerformanceNavigationTiming")}} برمی‌گرداند.

## سینتکس

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PerformanceNavigationTiming")}} است.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformanceNavigationTiming` برمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ entryTypes: ["navigation"] });
```

این کار یک شیء JSON به شکل زیر را در کنسول ثبت می‌کند:

```json
{
  "name": "https://en.wikipedia.org/wiki/Main_Page",
  "entryType": "navigation",
  "startTime": 0,
  "duration": 227.60000002384186,
  "initiatorType": "navigation",
  "nextHopProtocol": "h2",
  "renderBlockingStatus": "blocking",
  "workerStart": 0,
  "redirectStart": 4,
  "redirectEnd": 71.40000000596046,
  "fetchStart": 71.40000000596046,
  "domainLookupStart": 71.40000000596046,
  "domainLookupEnd": 71.40000000596046,
  "connectStart": 71.40000000596046,
  "connectEnd": 71.40000000596046,
  "secureConnectionStart": 71.40000000596046,
  "requestStart": 73.7000000178814,
  "responseStart": 102.90000000596046,
  "responseEnd": 105.2000000178814,
  "transferSize": 19464,
  "encodedBodySize": 19164,
  "decodedBodySize": 83352,
  "serverTiming": [
    {
      "name": "cache",
      "duration": 0,
      "description": "hit-front"
    },
    {
      "name": "host",
      "duration": 0,
      "description": "cp3062"
    }
  ],
  "unloadEventStart": 0,
  "unloadEventEnd": 0,
  "domInteractive": 178.10000002384186,
  "domContentLoadedEventStart": 178.2000000178814,
  "domContentLoadedEventEnd": 178.2000000178814,
  "domComplete": 227.60000002384186,
  "loadEventStart": 227.60000002384186,
  "loadEventEnd": 227.60000002384186,
  "type": "navigate",
  "redirectCount": 1,
  "activationStart": 0,
  "confidence": {
    "randomizedTriggerRate": 0.4994798,
    "value": "high"
  }
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}