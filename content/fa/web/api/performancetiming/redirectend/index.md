---
title: "PerformanceTiming: redirectEnd property"
short-title: redirectEnd
slug: Web/API/PerformanceTiming/redirectEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.redirectEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط کاربری (interface) در [نسخه دوم مشخصات زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

خاصیت فقط خواندنی قدیمی **`PerformanceTiming.redirectEnd`** یک `unsigned long long` را برمی‌گرداند که نشان‌دهنده لحظه‌ای (به میلی‌ثانیه از مبدأ UNIX) است که آخرین تغییرمسیر HTTP کامل شده است؛ یعنی زمانی که آخرین بایت از پاسخ HTTP دریافت شده است. اگر هیچ تغییرمسیری وجود نداشته باشد، یا اگر یکی از تغییرمسیرها از همان مبدأ (same origin) نباشد، مقدار بازگشتی `0` خواهد بود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("Performance")}} که این خاصیت به آن تعلق دارد.