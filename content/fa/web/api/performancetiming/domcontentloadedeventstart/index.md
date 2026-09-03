---
title: "PerformanceTiming: domContentLoadedEventStart property"
short-title: domContentLoadedEventStart
slug: Web/API/PerformanceTiming/domContentLoadedEventStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domContentLoadedEventStart
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط (interface) این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط خواندنی قدیمی **`PerformanceTiming.domContentLoadedEventStart`** یک `unsigned long long` را برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای (به میلی‌ثانیه از مبدأ UNIX) درست قبل از اینکه تحلیل‌گر (parser) رویداد {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}} را ارسال کند، یعنی درست بعد از اجرای تمام اسکریپت‌هایی که باید بلافاصله پس از تحلیل اجرا شوند.

## Value

یک `unsigned long long`.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.