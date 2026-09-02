```markdown
---
title: "LayoutShiftAttribution: toJSON() method"
short-title: toJSON()
slug: Web/API/LayoutShiftAttribution/toJSON
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.LayoutShiftAttribution.toJSON
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

متد **`toJSON()`** از رابط {{domxref("LayoutShiftAttribution")}} یک _سریال‌ساز_ است که یک نمایش JSON از شیء `LayoutShiftAttribution` بازمی‌گرداند.

## نحو (Syntax)

```js-nolint
toJSON()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء JSON که سریال‌سازی شیء {{domxref("LayoutShiftAttribution")}} است.

## مثال‌ها

مثال زیر یک نمایش JSON از اولین آیتم در {{domxref("LayoutShift.sources")}} را در کنسول چاپ می‌کند.

```js
new PerformanceObserver((list) => {
  for (const { sources } of list.getEntries()) {
    if (sources) {
      console.log(sources[0].toJSON());
    }
  }
}).observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```