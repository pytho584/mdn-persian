---
title: "PerformanceTiming: domainLookupStart property"
---

---
title: "PerformanceTiming: domainLookupStart property"
short-title: domainLookupStart
slug: Web/API/PerformanceTiming/domainLookupStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domainLookupStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطِ این ویژگی در [مشخصات سطح ۲ زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی
**`PerformanceTiming.domainLookupStart`**
یک مقدار `unsigned long long` را برمی‌گرداند که لحظه شروع جستجوی دامنه (domain lookup) را بر حسب میلی‌ثانیه از شروع عصر یونیکس (UNIX epoch) نشان می‌دهد. اگر از اتصال پایدار (persistent connection) استفاده شود، یا اطلاعات در حافظه نهان (cache) یا یک منبع محلی ذخیره شده باشد، مقدار آن با {{domxref("PerformanceTiming.fetchStart")}} یکسان خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.