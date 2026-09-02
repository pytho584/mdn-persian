---
title: "LayoutShiftAttribution: node property"
---

---
title: "LayoutShiftAttribution: node property"
short-title: node
slug: Web/API/LayoutShiftAttribution/node
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShiftAttribution.node
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`node`** از رابط {{domxref("LayoutShiftAttribution")}} یک {{domxref("Node")}} را برمی‌گرداند که نشان‌دهنده شیء جابجا شده است.

## مقدار

یک {{domxref("Node")}}.

## مثال‌ها

مثال زیر `node` اولین آیتم در {{domxref("LayoutShift.sources")}} را در کنسول چاپ می‌کند.

```js
new PerformanceObserver((list) => {
  for (const { sources } of list.getEntries()) {
    if (sources) {
      console.log(sources[0].node);
    }
  }
}).observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}