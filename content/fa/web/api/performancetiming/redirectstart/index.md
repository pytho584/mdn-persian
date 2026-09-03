---
title: "PerformanceTiming: redirectStart property"
---

---
title: "PerformanceTiming: redirectStart property"
short-title: redirectStart
slug: Web/API/PerformanceTiming/redirectStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.redirectStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابط این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‌خواندنی قدیمی **`PerformanceTiming.redirectStart`** یک مقدار `unsigned long long` برمی‌گرداند که بیانگر لحظهٔ شروع اولین تغییرمسیر HTTP، بر حسب میلی‌ثانیه از مبدأ UNIX است. اگر هیچ تغییرمسیری وجود نداشته باشد، یا اگر یکی از تغییرمسیرها از همان مبدأ نباشد، مقدار بازگردانده‌شده `0` خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.