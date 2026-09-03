---
title: "PerformanceMark: detail property"
short-title: detail
slug: Web/API/PerformanceMark/detail
page-type: web-api-instance-property
browser-compat: api.PerformanceMark.detail
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`detail`** فراداده‌های دلخواهی را برمی‌گرداند که هنگام ساخت علامت (mark) در آن گنجانده شده است (چه هنگام استفاده از {{domxref("Performance.mark","performance.mark()")}} چه سازنده {{domxref("PerformanceMark.PerformanceMark","PerformanceMark()")}}).

## مقدار

مقداری را که روی آن تنظیم شده است برمی‌گرداند (از `markOptions` مربوط به {{domxref("Performance.mark","performance.mark()")}} یا سازنده {{domxref("PerformanceMark.PerformanceMark","PerformanceMark()")}}).

## مثال‌ها

مثال زیر ویژگی `detail` را نشان می‌دهد:

```js
performance.mark("dog", { detail: "labrador" });

const dogEntries = performance.getEntriesByName("dog");

dogEntries[0].detail; // labrador
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}