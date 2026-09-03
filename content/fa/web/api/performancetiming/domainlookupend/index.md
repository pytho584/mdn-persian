---
title: "PerformanceTiming: domainLookupEnd property"
short-title: domainLookupEnd
slug: Web/API/PerformanceTiming/domainLookupEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domainLookupEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این ویژگی از این رابط در [نسخهٔ دوم مشخصات Navigation Timing](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنیِ قدیمی **`PerformanceTiming.domainLookupEnd`** یک `unsigned long long` برمی‌گرداند که لحظهٔ پایان جستجوی دامنه را بر حسب میلی‌ثانیه از مبدأ یونیکس (UNIX epoch) نشان می‌دهد. اگر از اتصال پایدار استفاده شود، یا اطلاعات در حافظهٔ پنهان (cache) یا یک منبع محلی ذخیره شده باشد، مقدار آن با {{domxref("PerformanceTiming.fetchStart")}} یکسان خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.