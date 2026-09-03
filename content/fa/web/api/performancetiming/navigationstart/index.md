---
title: "PerformanceTiming: navigationStart property"
short-title: navigationStart
slug: Web/API/PerformanceTiming/navigationStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.navigationStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطِ مربوط به این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است.
> لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگیِ قدیمیِ فقط‌خواندنی **`PerformanceTiming.navigationStart`** یک مقدار `unsigned long long` برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای بر حسب میلی‌ثانیه از مبدأ یونیکس (UNIX epoch) است؛ دقیقاً پس از آن‌که اعلانِ unload (تخلیه) برای سند قبلی در همان بافت مرور (browsing context) پایان می‌یابد. اگر سند قبلی‌ای وجود نداشته باشد، این مقدار با {{domxref("PerformanceTiming.fetchStart")}} یکسان خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.