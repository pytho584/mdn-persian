---
title: "PerformanceTiming: domLoading property"
---

---
title: "PerformanceTiming: domLoading property"
short-title: domLoading
slug: Web/API/PerformanceTiming/domLoading
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domLoading
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> رابطِ مربوط به این ویژگی در [مشخصات سطح ۲ زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

خصوصیت فقط‌خواندنی قدیمی **`PerformanceTiming.domLoading`** یک مقدار `unsigned long long` برمی‌گرداند که نشان‌دهنده لحظه‌ای (به میلی‌ثانیه از مبدأ UNIX) است که تجزیه‌گر کار خود را آغاز می‌کند؛ یعنی زمانی که {{domxref("Document.readyState")}} به `'loading'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} صادر می‌شود.

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.