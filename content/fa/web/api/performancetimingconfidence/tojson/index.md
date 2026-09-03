---
title: "PerformanceTimingConfidence: toJSON() method"
short-title: toJSON()
slug: Web/API/PerformanceTimingConfidence/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PerformanceTimingConfidence.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** در رابط {{domxref("PerformanceTimingConfidence")}} یک {{Glossary("Serialization","serializer")}} (سریال‌ساز) است که بازنمایی JSON از شیء {{domxref("PerformanceTimingConfidence")}} را برمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که حاصل سریال‌سازیِ شیء {{domxref("PerformanceTimingConfidence")}} است.

## مثال‌ها

### استفاده از متد toJSON

این مثال از یک {{domxref("PerformanceObserver")}} برای دریافت سریال‌سازی JSON از داده‌های اطمینانِ ورودی‌های {{domxref("PerformanceNavigationTiming")}} که مشاهده شده‌اند استفاده می‌کند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.confidence.toJSON());
  });
});

observer.observe({ type: "navigation", buffered: true });
```

این کار شیء JSON زیر را در کنسول ثبت می‌کند:

```json
{
  "randomizedTriggerRate": 0.4994798,
  "value": "high"
}
```

برای دریافت یک رشته‌ی JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این تابع به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceTimingConfidence")}}
- {{jsxref("JSON")}}