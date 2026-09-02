---
title: "LayoutShift: sources property"
short-title: sources
slug: Web/API/LayoutShift/sources
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShift.sources
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط خواندنی **`sources`** در رابط {{domxref("LayoutShift")}} یک آرایه از اشیاء {{domxref("LayoutShiftAttribution")}} برمی‌گرداند که عناصر DOM جابه‌جا شده در طول تغییر مکان طرح‌بندی را مشخص می‌کنند.

## مقدار

یک {{jsxref("Array")}} از اشیاء {{domxref("LayoutShiftAttribution")}}. این آرایه بیش از پنج منبع را شامل نخواهد شد. اگر بیش از پنج عنصر تحت تأثیر تغییر مکان طرح‌بندی قرار گرفته باشند، پنج عنصر با بیشترین تأثیر گزارش می‌شوند.

## مثال‌ها

### ثبت منابع تغییر مکان طرح‌بندی

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.sources.forEach((source) => {
      console.log(source);
    });
  });
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LayoutShiftAttribution")}}