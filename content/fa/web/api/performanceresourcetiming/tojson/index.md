---
title: "PerformanceResourceTiming: toJSON() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/PerformanceResourceTiming/toJSON"
---

---
title: "PerformanceResourceTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceResourceTiming/toJSON
page-type: web-api-instance-method
browser-compat: api.PerformanceResourceTiming.toJSON
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`toJSON()`** در رابط {{domxref("PerformanceResourceTiming")}} یک {{Glossary("Serialization","سریالساز")}} است؛ این متد نمایش JSON از شیء {{domxref("PerformanceResourceTiming")}} را بازمیگرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریالسازی شیء {{domxref("PerformanceResourceTiming")}} است.

## مثالها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `PerformanceResourceTiming` بازمیگرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "resource", buffered: true });
```

این کار یک شیء JSON مانند زیر را در کنسول ثبت میکند:

```json
{
  "name": "https://upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/31px-Commons-logo.svg.png",
  "entryType": "resource",
  "startTime": 110.80000001192093,
  "duration": 11.599999994039536,
  "initiatorType": "img",
  "nextHopProtocol": "h2",
  "renderBlockingStatus": "non-blocking",
  "workerStart": 0,
  "redirectStart": 0,
  "redirectEnd": 0,
  "fetchStart": 110.80000001192093,
  "domainLookupStart": 110.80000001192093,
  "domainLookupEnd": 110.80000001192093,
  "connectStart": 110.80000001192093,
  "connectEnd": 110.80000001192093,
  "secureConnectionStart": 110.80000001192093,
  "requestStart": 117.30000001192093,
  "responseStart": 120.40000000596046,
  "responseStatus": 200,
  "responseEnd": 122.40000000596046,
  "transferSize": 0,
  "encodedBodySize": 880,
  "decodedBodySize": 880,
  "serverTiming": [
    {
      "name": "cache",
      "duration": 0,
      "description": "hit-front"
    },
    {
      "name": "host",
      "duration": 0,
      "description": "cp3061"
    }
  ]
}
```

برای دریافت رشته JSON میتوانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد بهطور خودکار `toJSON()` را فراخوانی میکند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}