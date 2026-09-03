---
title: "PerformanceTiming: secureConnectionStart property"
short-title: secureConnectionStart
slug: Web/API/PerformanceTiming/secureConnectionStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.secureConnectionStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطِ این ویژگی در [نسخهٔ دوم مشخصات زمانبندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً بهجای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقطخواندنی قدیمی **`PerformanceTiming.secureConnectionStart`** یک `unsigned long long` برمیگرداند که لحظهٔ شروع دستدادن اتصال امن را بر حسب میلیثانیه از مبدأ یونیکس (UNIX epoch) نشان میدهد. اگر چنین اتصالی درخواست نشده باشد، مقدار `0` برمیگرداند.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.