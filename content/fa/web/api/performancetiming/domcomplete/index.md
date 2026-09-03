---
title: "PerformanceTiming: domComplete property"
short-title: domComplete
slug: Web/API/PerformanceTiming/domComplete
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domComplete
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این واسط (interface) از این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از واسط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط خواندنی قدیمی
**`PerformanceTiming.domComplete`**
یک `unsigned long long` را برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای (به میلی‌ثانیه از زمان یونیکس) است که تجزیه‌گر (parser) کار خود را روی سند اصلی تمام کرده است؛ یعنی زمانی که {{domxref("Document.readyState")}} آن به `'complete'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} پرتاب می‌شود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- واسط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.