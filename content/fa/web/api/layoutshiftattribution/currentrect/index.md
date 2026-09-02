---
title: "LayoutShiftAttribution: currentRect property"
short-title: currentRect
slug: Web/API/LayoutShiftAttribution/currentRect
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShiftAttribution.currentRect
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`currentRect`** از رابط {{domxref("LayoutShiftAttribution")}}، یک شیء {{domxref("DOMRectReadOnly")}} را برمی‌گرداند که موقعیت عنصر را پس از جابه‌جایی نشان می‌دهد.

## مقدار

یک شیء {{domxref("DOMRectReadOnly")}}.

## مثال‌ها

مثال زیر، `currentRect` اولین مورد در {{domxref("LayoutShift.sources")}} را در کنسول چاپ می‌کند.

```js
new PerformanceObserver((list) => {
  for (const { sources } of list.getEntries()) {
    if (sources) {
      console.log(sources[0].currentRect);
    }
  }
}).observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}