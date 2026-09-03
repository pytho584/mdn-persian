---
title: "PerformanceTiming: responseEnd property"
short-title: responseEnd
slug: Web/API/PerformanceTiming/responseEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.responseEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابط مربوط به این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

**`PerformanceTiming.responseEnd`** یک ویژگی فقط‌خواندنی قدیمی است که یک مقدار `unsigned long long` برمی‌گرداند. این مقدار نشان‌دهندهٔ لحظه‌ای به میلی‌ثانیه از مبدأ زمان یونیکس است که مرورگر آخرین بایت پاسخ را از سرور، از حافظهٔ نهان (cache) یا از یک منبع محلی دریافت کرده است؛ اگر بسته‌شدن اتصال زودتر از دریافت آخرین بایت رخ داده باشد، این مقدار، زمان بسته‌شدن اتصال را بازمی‌گرداند.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.