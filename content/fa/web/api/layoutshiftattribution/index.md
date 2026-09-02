```markdown
---
title: LayoutShiftAttribution
slug: Web/API/LayoutShiftAttribution
page-type: web-api-interface
status:
  - experimental
browser-compat: api.LayoutShiftAttribution
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابطه `LayoutShiftAttribution` اطلاعات اشکال‌زدایی درباره عناصری که جابه‌جا شده‌اند را فراهم می‌کند.

با فراخوانی {{domxref("LayoutShift.sources")}}، نمونه‌هایی از `LayoutShiftAttribution` در یک آرایه بازگردانده می‌شوند.

## ویژگی‌های نمونه

- {{domxref("LayoutShiftAttribution.node")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : عنصری که جابه‌جا شده است را برمی‌گرداند (در صورت حذف شدن، `null`).
- {{domxref("LayoutShiftAttribution.previousRect")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("DOMRectReadOnly")}} برمی‌گرداند که موقعیت عنصر را قبل از جابه‌جایی نشان می‌دهد.
- {{domxref("LayoutShiftAttribution.currentRect")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("DOMRectReadOnly")}} برمی‌گرداند که موقعیت عنصر را بعد از جابه‌جایی نشان می‌دهد.

## روش‌های نمونه

- {{domxref("LayoutShiftAttribution.toJSON()")}} {{Experimental_Inline}}
  - : یک نمایش JSON از شیء `LayoutShiftAttribution` را برمی‌گرداند.

## مثال‌ها

مثال زیر تغییرات چیدمان (layout shifts) را مشاهده می‌کند و تأثیرگذارترین عنصر را شناسایی می‌کند. آرایه `sources` بر اساس ناحیه تأثیر، به ترتیب نزولی مرتب می‌شود — بنابراین اولین عنصر (`sources[0]`) عنصری را نشان می‌دهد که بیشترین سهم را در جابه‌جایی چیدمان داشته است. برای جزئیات بیشتر، به [اشکال‌زدایی Web Vitals در میدان عمل](https://web.dev/articles/debug-performance-in-the-field) مراجعه کنید.

```js
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    if (!entry.sources || entry.sources.length === 0) continue;

    const mostImpactfulSource = entry.sources[0];
    console.log("Layout shift score:", entry.value);
    console.log("Most impactful element:", largestShiftSource.node);
    console.log("Previous position:", largestShiftSource.previousRect);
    console.log("Current position:", largestShiftSource.currentRect);
  }
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [اشکال‌زدایی جابه‌جایی‌های چیدمان](https://web.dev/articles/debug-layout-shifts)
- [اشکال‌زدایی Web Vitals در میدان عمل](https://web.dev/articles/debug-performance-in-the-field)
```