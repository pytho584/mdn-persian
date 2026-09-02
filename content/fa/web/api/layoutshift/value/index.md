---
title: "LayoutShift: value property"
short-title: value
slug: Web/API/LayoutShift/value
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.LayoutShift.value
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

خاصیت فقط‌خواندنی **`value`** در رابط {{domxref("LayoutShift")}} امتیاز تغییر چیدمان (layout shift score) را برمی‌گرداند که از ضرب کسر تأثیر (بخشی از viewport که جابه‌جا شده است) در کسر فاصله (میزان جابه‌جایی به‌صورت کسری از viewport) به دست می‌آید.

## مقدار

عددی بین `0.0` و `1.0` که امتیاز تغییر چیدمان را نشان می‌دهد.

این مقدار از ضرب کسر تأثیر (بخشی از viewport که جابه‌جا شده است) در کسر فاصله (میزان جابه‌جایی به‌صورت کسری از viewport) محاسبه می‌شود.

```plain
layout shift score = impact fraction * distance fraction
```

برای جزئیات بیشتر، [Layout shift score](https://web.dev/articles/cls#layout_shift_score) را در web.dev ببینید.

## مثال‌ها

### ثبت امتیاز تغییر چیدمانِ ورودی

مثال زیر نحوه استفاده از خاصیت `value` برای ثبت امتیاز تغییر چیدمان را نشان می‌دهد.

```js
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    // Count layout shifts without recent user input only
    if (!entry.hadRecentInput) {
      console.log("Entry's layout shift score:", entry.value);
    }
  }
});

observer.observe({ type: "layout-shift", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}