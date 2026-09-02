---
title: "LargestContentfulPaint: toJSON() method"
short-title: toJSON()
slug: Web/API/LargestContentfulPaint/toJSON
page-type: web-api-instance-method
browser-compat: api.LargestContentfulPaint.toJSON
---

{{APIRef("Performance API")}}

متد **`toJSON()`** در رابط {{domxref("LargestContentfulPaint")}} یک {{Glossary("Serialization","سریال‌ساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("LargestContentfulPaint")}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که حاصل سریال‌سازی شیء {{domxref("LargestContentfulPaint")}} است.

این JSON شامل ویژگی {{domxref("LargestContentfulPaint.element", "element")}} نیست، زیرا آن ویژگی از نوع {{domxref("Element")}} است که عملیات `toJSON()` را ارائه نمی‌دهد.

## مثال‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `LargestContentfulPaint` برمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "largest-contentful-paint", buffered: true });
```

این کار شیء JSON زیر را در کنسول ثبت می‌کند:

```json
{
  "name": "",
  "entryType": "largest-contentful-paint",
  "startTime": 468.2,
  "duration": 0,
  "size": 19824,
  "renderTime": 468.2,
  "loadTime": 0,
  "id": "",
  "url": ""
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به‌طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}