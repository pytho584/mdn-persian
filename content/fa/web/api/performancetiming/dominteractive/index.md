---
title: "PerformanceTiming: domInteractive property"
short-title: domInteractive
slug: Web/API/PerformanceTiming/domInteractive
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.domInteractive
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط (interface) از این ویژگی در [مشخصات Navigation Timing Level 2](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

ویژگی فقط خواندنی قدیمی
**`PerformanceTiming.domInteractive`**
یک `unsigned long long` را برمی‌گرداند که نشان‌دهندهٔ لحظه‌ای (بر حسب میلی‌ثانیه از مبدأ UNIX) است که تحلیل‌گر (parser) کار خود را روی سند اصلی به پایان رسانده است؛ یعنی زمانی که {{domxref("Document.readyState")}} آن به `'interactive'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} صادر می‌شود.

از این ویژگی می‌توان برای اندازه‌گیری سرعت بارگذاری وب‌سایت‌هایی که کاربران _احساس_ می‌کنند استفاده کرد. با این حال چند نکته وجود دارد که اگر اسکریپت‌ها رندر را مسدود کنند و به صورت ناهمگام یا با فونت‌های وب سفارشی بارگذاری نشوند، رخ می‌دهد. قبل از استفاده از این ویژگی به عنوان معیاری برای تجربهٔ کاربری از سرعت بارگذاری یک وب‌سایت، [بررسی کنید که آیا در یکی از این موارد قرار دارید](https://www.stevesouders.com/blog/2015/08/07/dominteractive-is-it-really/).

## مقدار

یک `unsigned long long`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PerformanceTiming")}} که این ویژگی به آن تعلق دارد.
- مقالهٔ «[domInteractive: is it? really?](https://www.stevesouders.com/blog/2015/08/07/dominteractive-is-it-really/)» که توضیح می‌دهد چه زمانی می‌توانید از این ویژگی به عنوان معیاری برای تجربهٔ کاربری از بارگذاری یک وب‌سایت استفاده کنید.