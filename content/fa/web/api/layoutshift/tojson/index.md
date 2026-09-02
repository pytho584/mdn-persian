---
title: "LayoutShift: toJSON() method"
---

---
title: "LayoutShift: toJSON() method"
short-title: toJSON()
slug: Web/API/LayoutShift/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LayoutShift.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** از رابط {{domxref("LayoutShift")}} یک {{Glossary("Serialization","serializer")}} است؛ این متد یک نمایش JSON از شیء {{domxref("LayoutShift")}} بازمی‌گرداند.

## نحو

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{jsxref("JSON")}} که سریال‌سازی شیء {{domxref("LayoutShift")}} است.

## نمونه‌ها

### استفاده از متد toJSON

در این مثال، فراخوانی `entry.toJSON()` یک نمایش JSON از شیء `LayoutShift` بازمی‌گرداند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "layout-shift", buffered: true });
```

این کار یک شیء JSON به صورت زیر را ثبت می‌کند:

```json
{
  "name": "",
  "entryType": "layout-shift",
  "startTime": 246.39999999850988,
  "duration": 0,
  "value": 0.0071167845054842215,
  "hadRecentInput": false,
  "lastInputTime": 0,
  "sources": [
    {
      "previousRect": {
        "x": 917,
        "y": 708,
        "width": 706,
        "height": 248,
        "top": 708,
        "right": 1623,
        "bottom": 956,
        "left": 917
      },
      "currentRect": {
        "x": 693,
        "y": 708,
        "width": 1154,
        "height": 472,
        "top": 708,
        "right": 1847,
        "bottom": 1180,
        "left": 693
      }
    }
  ]
}
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به طور خودکار `toJSON()` را فراخوانی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("JSON")}}