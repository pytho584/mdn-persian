---
title: "PerformanceTiming: loadEventEnd property"
short-title: loadEventEnd
slug: Web/API/PerformanceTiming/loadEventEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.loadEventEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این ویژگی در [مشخصات سطح ۲ زمان‌بندی پیمایش](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از ویژگی فقط‌خواندنی {{domxref("PerformanceNavigationTiming.loadEventEnd")}} در رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی
**`PerformanceTiming.loadEventEnd`**
یک `unsigned long long` برمی‌گرداند که نشان‌دهنده لحظه‌ای (به میلی‌ثانیه از مبدأ UNIX) است که مدیریت‌کننده رویداد {{domxref("Window/load_event", "load")}} پایان یافته است؛ یعنی زمانی که رویداد load تکمیل شده است. اگر این رویداد هنوز ارسال نشده باشد یا هنوز کامل نشده باشد، مقدار `0` برمی‌گرداند.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.