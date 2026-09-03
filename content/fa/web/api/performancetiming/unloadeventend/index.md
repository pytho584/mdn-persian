---
title: "PerformanceTiming: unloadEventEnd property"
short-title: unloadEventEnd
slug: Web/API/PerformanceTiming/unloadEventEnd
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.unloadEventEnd
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط (interface) در [نسخه ۲ مشخصات زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط‑خواندنی قدیمی
**`PerformanceTiming.unloadEventEnd`**
یک `unsigned long long` را برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای (بر حسب میلی‌ثانیه از مبدأ UNIX) است که مدیریت‌کنندهٔ رویداد {{domxref("Window/unload_event", "unload")}} پایان می‌یابد. اگر سند قبلی وجود نداشته باشد، یا سند قبلی (یا یکی از تغییرمسیرهای مورد نیاز) از مبدأ یکسانی نباشد، مقدار بازگشتی `0` است.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.