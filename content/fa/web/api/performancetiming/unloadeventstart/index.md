---
title: "PerformanceTiming: unloadEventStart property"
short-title: unloadEventStart
slug: Web/API/PerformanceTiming/unloadEventStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.unloadEventStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط کاربری (interface) این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ (deprecated) شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط خواندنی (read-only) قدیمی
**`PerformanceTiming.unloadEventStart`**
یک `unsigned long long` را برمی‌گرداند که نشان‌دهنده لحظه‌ای (به میلی‌ثانیه از مبدأ UNIX) است که رویداد {{domxref("Window/unload_event", "unload")}} پرتاب شده است. اگر سند قبلی وجود نداشته باشد، یا اگر سند قبلی، یا یکی از تغییر مسیرهای (redirects) مورد نیاز، از همان مبدأ (same origin) نباشد، مقدار بازگشتی `0` خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.