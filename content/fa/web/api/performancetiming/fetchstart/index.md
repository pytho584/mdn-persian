---
title: "PerformanceTiming: fetchStart property"
short-title: fetchStart
slug: Web/API/PerformanceTiming/fetchStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.fetchStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطِ مربوط به این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی منسوخ **`PerformanceTiming.fetchStart`** یک `unsigned long long` برمی‌گرداند که لحظه‌ای را بر حسب میلی‌ثانیه از مبدأ UNIX نشان می‌دهد که مرورگر آماده است سند را با استفاده از یک درخواست HTTP واکشی کند. این لحظه _پیش از_ بررسی هرگونه حافظهٔ پنهانِ برنامه (application cache) است.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.