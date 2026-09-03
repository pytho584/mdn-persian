---
title: "PerformanceTiming: loadEventStart property"
short-title: loadEventStart
slug: Web/API/PerformanceTiming/loadEventStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.loadEventStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> واسطی که این ویژگی به آن تعلق دارد، در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از ویژگی فقط‌خواندنی {{domxref("PerformanceNavigationTiming.loadEventStart")}} در واسط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی **`PerformanceTiming.loadEventStart`** یک `unsigned long long` برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای است (برحسب میلی‌ثانیه از مبدأ یونیکس) که رویداد {{domxref("Window/load_event", "load")}} برای سند جاری ارسال شده است. اگر این رویداد هنوز ارسال نشده باشد، مقدار `0` برگردانده می‌شود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- واسط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.