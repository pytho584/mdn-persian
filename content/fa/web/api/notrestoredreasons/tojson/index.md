---
title: "NotRestoredReasons: toJSON() method"
short-title: toJSON()
slug: Web/API/NotRestoredReasons/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NotRestoredReasons.toJSON
spec-urls: https://html.spec.whatwg.org/multipage/nav-history-apis.html#notrestoredreasons
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

روش **`toJSON()`** از رابط {{domxref("NotRestoredReasons")}} یک {{Glossary("Serialization","سریال‌ساز (serializer)")}} است؛ این روش یک نمایش JSON از شیء {{domxref("NotRestoredReasons")}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("NotRestoredReasons")}} است.

## مثال‌ها

تابع زیر یک نمایش JSON از شیء `NotRestoredReasons` اولین شیء `PerformanceNavigationTiming` که در حال حاضر در performance timeline وجود دارد، برمی‌گرداند:

```js
function returnNRR() {
  const navEntries = performance.getEntriesByType("navigation");
  let navEntry = navEntries[0];
  return navEntry.notRestoredReasons.toJSON();
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}
- [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}