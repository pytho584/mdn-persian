---
title: "LayoutShift: hadRecentInput property"
short-title: hadRecentInput
slug: Web/API/LayoutShift/hadRecentInput
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShift.hadRecentInput
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

ویژگی فقط‌خواندنی **`hadRecentInput`** از رابط {{domxref("LayoutShift")}} مقدار `true` را برمی‌گرداند اگر {{domxref("LayoutShift.lastInputTime", "lastInputTime")}} در ۵۰۰ میلی‌ثانیهٔ گذشته رخ داده باشد.

تغییرات چیدمان (layout shifts) تنها زمانی مشکل‌ساز هستند که کاربر انتظار آن‌ها را نداشته باشد؛ بنابراین تغییرات چیدمان ناشی از تعامل‌های کاربر (مانند زمانی که کاربر یک عنصر واسط کاربر را باز می‌کند) معمولاً در معیارهای تغییر چیدمان لحاظ نمی‌شوند. خاصیت `hadRecentInput` به شما امکان می‌دهد این تغییرات را از محاسبه خارج کنید.

## مقدار

یک مقدار بولی که اگر {{domxref("LayoutShift.lastInputTime", "lastInputTime")}} در ۵۰۰ میلی‌ثانیهٔ گذشته رخ داده باشد، `true` را برمی‌گرداند؛ در غیر این صورت `false`.

## مثال‌ها

### نادیده گرفتن ورودی اخیر کاربر برای امتیازهای تغییر چیدمان

مثال زیر نشان می‌دهد که چگونه از خاصیت `hadRecentInput` برای شمارش فقط تغییرات چیدمان بدون ورودی اخیر کاربر استفاده می‌شود.

```js
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    // Count layout shifts without recent user input only
    if (!entry.hadRecentInput) {
      console.log("LayoutShift value:", entry.value);
      if (entry.sources) {
        for (const { node, currentRect, previousRect } of entry.sources)
          console.log("LayoutShift source:", node, {
            currentRect,
            previousRect,
          });
      }
    }
  }
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LayoutShift.lastInputTime")}}