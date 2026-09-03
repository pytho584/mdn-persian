---
title: "Resource timing"
---

---
title: Resource timing
slug: Web/API/Performance_API/Resource_timing
page-type: web-api-overview
---

{{DefaultAPISidebar("Performance API")}}

Resource Timing بخشی از Performance API است و امکان دریافت و تحلیل داده‌های زمانی دقیق شبکه را برای بارگذاری منابع یک برنامه فراهم می‌کند. برای نمونه، یک برنامه می‌تواند با استفاده از معیارهای زمان‌بندی تعیین کند که بارگذاری یک منبع خاص (مانند تصویر یا اسکریپت) چقدر طول می‌کشد؛ چه این بارگذاری به‌صورت ضمنی و به‌عنوان بخشی از بارگذاری صفحه انجام شود، چه به‌صورت صریح از طریق جاوااسکریپت، مثلاً با API واکشی {{domxref("Window/fetch", "fetch()")}}.

هر منبع در یک سند با یک ورودی {{domxref("PerformanceResourceTiming")}} (که رابط {{domxref("PerformanceEntry")}} را گسترش می‌دهد) و با {{domxref("PerformanceEntry.entryType","entryType")}} برابر با `"resource"` نمایش داده می‌شود.

برای هر ورودی `PerformanceResourceTiming`، یک _خط زمانی بارگذاری منبع_ ثبت می‌شود؛ این خط زمانی شامل {{domxref("DOMHighResTimeStamp","high-resolution timestamps", "", 1)}} برای رویدادهای شبکه مانند زمان شروع و پایان تغییر مسیر، زمان شروع و پایان جست‌وجوی DNS، زمان شروع درخواست، زمان شروع و پایان پاسخ و غیره است. افزون بر مهرهای زمانی، ویژگی‌های دیگری نیز درباره منبع در این ورودی ثبت می‌شود؛ از جمله اندازه منبع واکشی‌شده یا نوع منبعی که واکشی را آغاز کرده است.

برای آشنایی با [معیارهای متداول زمان‌بندی منابع](/en-US/docs/Web/API/PerformanceResourceTiming#typical_resource_timing_metrics)، به صفحه مرجع رابط {{domxref("PerformanceResourceTiming")}} مراجعه کنید.

## مهرهای زمانی بارگذاری منابع

![نمودار مهرهای زمانی که ترتیب ثبت آن‌ها را هنگام واکشی یک منبع نشان می‌دهد](https://mdn.github.io/shared-assets/images/diagrams/api/performance/resource-timing/timestamp-diagram.svg)
شکل ۱. مهرهای زمانی بارگذاری منابع ([منبع](https://w3c.github.io/resource-timing/#attribute-descriptions)).

یک برنامه می‌تواند مهرهای زمانی مراحل مختلف بارگذاری یک منبع را به‌دست آورد؛ مثلاً {{domxref('PerformanceEntry.startTime','startTime')}}، مهرهای زمانی DNS، زمان برقراری اتصال و سپس زمان‌های مختلف دانلود منبع.

بخش [مهرهای زمانی](/en-US/docs/Web/API/PerformanceResourceTiming#timestamps) در صفحه مرجع رابط {{domxref("PerformanceResourceTiming")}} را ببینید.

## اندازه منبع

رابط {{domxref("PerformanceResourceTiming")}} سه ویژگی دارد که می‌توان برای به‌دست آوردن داده‌های اندازه منبع از آن‌ها استفاده کرد. ویژگی {{domxref('PerformanceResourceTiming.transferSize','transferSize')}} اندازه (به بایت) منبع واکشی‌شده را برمی‌گرداند؛ این اندازه شامل فیلدهای هدر پاسخ و بدنه بار پاسخ است.

ویژگی {{domxref('PerformanceResourceTiming.encodedBodySize','encodedBodySize')}} اندازه (به اکتت) _بدنه بار_ دریافت‌شده از فرایند واکشی (HTTP یا حافظه پنهان) را **پیش از** حذف کدگذاری‌های محتوای اعمال‌شده برمی‌گرداند. ویژگی {{domxref('PerformanceResourceTiming.decodedBodySize','decodedBodySize')}} اندازه (به اکتت) _بدنه پیام_ دریافت‌شده از فرایند واکشی (HTTP یا حافظه پنهان) را **پس از** حذف کدگذاری‌های محتوای اعمال‌شده برمی‌گرداند.

## سایر ویژگی‌ها

رابط {{domxref("PerformanceResourceTiming")}} [اطلاعات تکمیلی منابع](/en-US/docs/Web/API/PerformanceResourceTiming#additional_resource_information) را نیز در اختیار شما قرار می‌دهد. برای فهرست کامل ویژگی‌ها، به مستندات مرجع مراجعه کنید.

## مدیریت اندازه بافر منابع

اگر وب‌سایت یا برنامه شما بیش از ۲۵۰ منبع را واکشی می‌کند و می‌خواهید بیش از ۲۵۰ ورودی {{domxref("PerformanceResourceTiming")}} ثبت شود، باید اندازه بافر زمان‌بندی منابع را افزایش دهید.

برای تنظیم اندازه بافر داده‌های کارایی منابع مرورگر، از متد {{domxref("Performance.setResourceTimingBufferSize()")}} و برای پاک‌کردن بافر داده‌های کارایی منابع مرورگر، از متد {{domxref("Performance.clearResourceTimings()")}} استفاده کنید.

برای دریافت اعلان هنگام پر شدن بافر زمان‌بندی منابع مرورگر، به رویداد {{domxref("Performance.resourcetimingbufferfull_event", "resourcetimingbufferfull")}} گوش دهید.

فراخوانی زیر امکان ثبت ۵۰۰ ورودی کارایی با نوع `"resource"` را در خط زمانی کارایی مرورگر فراهم می‌کند.

```js
performance.setResourceTimingBufferSize(500);
```

برای اطلاعات بیشتر، همچنین به [مدیریت اندازه بافرها](/en-US/docs/Web/API/Performance_API/Performance_data#managing_buffer_sizes) مراجعه کنید.

## اطلاعات زمان‌بندی مبدأ متقاطع

بسیاری از ویژگی‌های زمان‌بندی منابع، وقتی منبع از طریق یک درخواست مبدأ متقاطع (cross-origin) دریافت شود، به بازگرداندن `0` یا رشته خالی محدود می‌شوند. برای در دسترس قرار دادن اطلاعات زمان‌بندی مبدأ متقاطع، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

برای اطلاع از فیلدهای متأثر، بخش [اطلاعات زمان‌بندی مبدأ متقاطع](/en-US/docs/Web/API/PerformanceResourceTiming#cross-origin_timing_information) را در صفحه مرجع رابط {{domxref("PerformanceResourceTiming")}} ببینید.

## جستارهای وابسته

- {{domxref("PerformanceResourceTiming")}}
- {{httpheader("Timing-Allow-Origin")}}
- {{domxref("Performance.setResourceTimingBufferSize()")}}
- {{domxref("Performance.clearResourceTimings()")}}