---
title: "LayoutShiftAttribution: previousRect property"
short-title: previousRect
slug: Web/API/LayoutShiftAttribution/previousRect
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShiftAttribution.previousRect
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`previousRect`** در رابط {{domxref("LayoutShiftAttribution")}} یک شیء {{domxref("DOMRectReadOnly")}} برمی‌گرداند که موقعیت عنصر را پیش از جابه‌جایی نشان می‌دهد.

## مقدار

یک شیء {{domxref("DOMRectReadOnly")}}.

## مثال‌ها

مثال زیر مقدار `previousRect` اولین مورد در {{domxref("LayoutShift.sources")}} را در کنسول چاپ می‌کند.

```js
new PerformanceObserver((list) => {
  for (const { sources } of list.getEntries()) {
    if (sources) {
      console.log(sources[0].previousRect);
    }
  }
}).observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}