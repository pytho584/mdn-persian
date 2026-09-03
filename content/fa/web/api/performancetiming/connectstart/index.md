---
title: "PerformanceTiming: connectStart property"
short-title: connectStart
slug: Web/API/PerformanceTiming/connectStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.connectStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطهای که این ویژگی به آن تعلق دارد در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً بهجای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی **`PerformanceTiming.connectStart`** یک `unsigned long long` برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای است، به میلی‌ثانیه از مبدأ یونیکس، که درخواست باز کردن یک اتصال به شبکه ارسال می‌شود. اگر لایهٔ انتقال خطایی گزارش دهد و برقراری اتصال دوباره آغاز شود، زمان شروع آخرین برقراری اتصال برگردانده می‌شود. اگر از اتصال پایدار (persistent connection) استفاده شود، مقدار این ویژگی با {{domxref("PerformanceTiming.fetchStart")}} یکسان خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.