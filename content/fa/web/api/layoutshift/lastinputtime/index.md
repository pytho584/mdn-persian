---
title: "LayoutShift: lastInputTime property"
short-title: lastInputTime
slug: Web/API/LayoutShift/lastInputTime
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShift.lastInputTime
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`lastInputTime`** در رابط {{domxref("LayoutShift")}} زمان آخرین ورودیِ استثنا شده را برمی‌گرداند، یا اگر هیچ ورودیِ استثنا شده‌ای رخ نداده باشد، مقدار `0` را برمی‌گرداند.

تغییرات چیدمان (layout shifts) تنها زمانی بد هستند که کاربر انتظار آن‌ها را نداشته باشد. معیارهای تغییر چیدمان مانند {{glossary("CLS")}} تغییراتی را که بلافاصله پس از تعاملات خاص کاربر رخ می‌دهند مستثنی می‌کنند. این تعاملات «ورودی‌های استثنا شده» (excluding inputs) نامیده می‌شوند. ورودی‌های استثنا شده عبارتند از:

- هر رویدادی که نشان‌دهنده تعامل فعال کاربر با سند باشد: ([`mousedown`](/en-US/docs/Web/API/Element/mousedown_event)، [`keydown`](/en-US/docs/Web/API/Element/keydown_event) و [`pointerdown`](/en-US/docs/Web/API/Element/pointerdown_event))
- هر رویدادی که مستقیماً اندازه viewport را تغییر دهد.
- رویدادهای [`change`](/en-US/docs/Web/API/HTMLElement/change_event).

رویدادهای [`mousemove`](/en-US/docs/Web/API/Element/mousemove_event) و [`pointermove`](/en-US/docs/Web/API/Element/pointermove_event) **ورودی‌های استثنا شده محسوب نمی‌شوند**.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان آخرین ورودی استثنا شده است، یا اگر هیچ ورودی استثنا شده‌ای رخ نداده باشد، مقدار `0`.

## مثال‌ها

### ثبت زمان‌های آخرین ورودی

زمان‌های ورودی استثنا شده را در صورت وقوع ثبت کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.lastInputTime) {
      console.log(entry.lastInputTime);
    }
  });
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("LayoutShift.hadRecentInput")}}