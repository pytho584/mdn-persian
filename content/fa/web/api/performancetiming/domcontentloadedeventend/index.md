---
title: "PerformanceTiming: domContentLoadedEventEnd property"
short-title: domContentLoadedEventEnd
slug: Web/API/PerformanceTiming/domContentLoadedEventEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domContentLoadedEventEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابط (interface) مربوط به این ویژگی در [مشخصات سطح ۲ زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ (deprecated) شده است. لطفاً به‌جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی قدیمی (legacy) **`PerformanceTiming.domContentLoadedEventEnd`** فقط‌خواندنی است و مقدار `unsigned long long` را برمی‌گرداند که لحظه‌ای را، بر حسب میلی‌ثانیه از مبدأ زمانی UNIX، نشان می‌دهد؛ این لحظه دقیقاً پس از اجرای همه اسکریپت‌هایی است که باید در سریع‌ترین زمان ممکن اجرا شوند، چه به‌ترتیب اجرا شده باشند و چه بدون ترتیب.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.