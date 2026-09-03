---
title: "PerformanceTiming: connectEnd property"
---

---
title: "PerformanceTiming: connectEnd property"
short-title: connectEnd
slug: Web/API/PerformanceTiming/connectEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.connectEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این ویژگی در [مشخصات سطح ۲ Navigation Timing](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی
**`PerformanceTiming.connectEnd`**
یک `unsigned long long` برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای، بر حسب میلی‌ثانیه از مبدأ UNIX، است که اتصال به شبکه برقرار شده است. اگر لایهٔ انتقال خطایی گزارش دهد و برقراری اتصال دوباره آغاز شود، زمان پایان آخرین تلاش برای برقراری اتصال داده می‌شود. اگر از اتصال پایدار (persistent connection) استفاده شود، مقدار آن با {{domxref("PerformanceTiming.fetchStart")}} یکسان خواهد بود. اتصال زمانی باز در نظر گرفته می‌شود که تمام مراحل دست‌دهی اتصال امن یا احراز هویت SOCKS پایان یافته باشد.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.