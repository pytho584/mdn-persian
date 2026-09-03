---
title: "NotRestoredReasonDetails: toJSON() method"
short-title: toJSON()
slug: Web/API/NotRestoredReasonDetails/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NotRestoredReasonDetails.toJSON
spec-urls: https://html.spec.whatwg.org/multipage/nav-history-apis.html#notrestoredreasondetails
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("NotRestoredReasonDetails")}} یک {{Glossary("Serialization","serializer")}} (سریال‌ساز) است؛ یک نمایش JSON از شیء {{domxref("NotRestoredReasonDetails")}} برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازیِ شیء {{domxref("NotRestoredReasonDetails")}} است.

## مثال‌ها

تابع زیر، نمایش JSON از اولین شیء `NotRestoredReasonDetails` از شیء `NotRestoredReasons` مربوط به اولین شیء `PerformanceNavigationTiming` را که در حال حاضر در بازه زمانی عملکرد (performance timeline) موجود است، برمی‌گرداند:

```js
function returnNRR() {
  const navEntries = performance.getEntriesByType("navigation");
  let navEntry = navEntries[0];
  return navEntry.notRestoredReasons.reasons[0].toJSON();
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}
- [Monitoring bfcache blocking reasons](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}