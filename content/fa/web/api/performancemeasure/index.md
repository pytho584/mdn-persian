---
title: PerformanceMeasure
slug: Web/API/PerformanceMeasure
page-type: web-api-interface
browser-compat: api.PerformanceMeasure
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

**`PerformanceMeasure`** یک _رابط انتزاعی_ برای اشیاء {{domxref("PerformanceEntry")}} است که {{domxref("PerformanceEntry.entryType","entryType")}} آن‌ها `"measure"` است. ورودی‌های این نوع با فراخوانی {{domxref("Performance.measure","performance.measure()")}} ایجاد می‌شوند تا یک {{domxref("DOMHighResTimeStamp")}} _نام‌دار_ (همان _اندازه‌گیری_) را بین دو _نشان_ به _خط زمانی کارایی_ مرورگر اضافه کنند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PerformanceMeasure.detail")}}
  - : شامل ابرداده‌های دلخواه دربارهٔ اندازه‌گیری است.

این رابط، ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} به ارث می‌برد و آن‌ها را به شکل زیر محدود می‌کند:

- {{domxref("PerformanceEntry.entryType")}}
  - : مقدار `"measure"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}}
  - : نامی را که هنگام ایجادِ اندازه‌گیری از طریق فراخوانی {{domxref("Performance.measure()","performance.measure()")}} به آن داده شده است، برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} را برمی‌گرداند که هنگام فراخوانی {{domxref("Performance.measure()","performance.measure()")}} به اندازه‌گیری داده شده است.
- {{domxref("PerformanceEntry.duration")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که مدت‌زمان اندازه‌گیری است (معمولاً timestamp نشانِ پایان منهای timestamp نشانِ آغاز).

## متدهای نمونه

این رابط هیچ متدی ندارد.

## مثال

مثال را در [استفاده از API زمان‌بندی کاربر](/en-US/docs/Web/API/Performance_API/User_timing) ببینید.

Chrome DevTools از `performance.measure()` و به‌ویژه از ویژگی ساختاریافتهٔ `detail` به‌عنوان بخشی از API توسعه‌پذیری خود استفاده می‌کند که این موارد را در ترک‌های سفارشی در traceهای کارایی نمایش می‌دهد. برای اطلاعات و مثال‌های بیشتر، به مثال در صفحهٔ [Performance: متد measure()](/en-US/docs/Web/API/Performance/measure) و [مستندات API توسعه‌پذیری Chrome](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_the_user_timings_api) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [User Timing (مرور کلی)](/en-US/docs/Web/API/Performance_API/User_timing)
- [استفاده از API زمان‌بندی کاربر](/en-US/docs/Web/API/Performance_API/User_timing)