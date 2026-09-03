---
title: "PerformanceTiming: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceTiming/toJSON
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.PerformanceTiming.toJSON
---

{{APIRef("Performance API")}}{{deprecated_header}}

> [!WARNING]
> این ویژگی در [نسخه دوم مشخصات Navigation Timing](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

متد قدیمی **`toJSON()`** در رابط {{domxref("PerformanceTiming")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PerformanceTiming")}} را برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("PerformanceTiming")}} است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}