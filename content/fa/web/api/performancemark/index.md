---
title: PerformanceMark
slug: Web/API/PerformanceMark
page-type: web-api-interface
browser-compat: api.PerformanceMark
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

**`PerformanceMark`** یک رابط (interface) برای اشیاء {{domxref("PerformanceEntry")}} با {{domxref("PerformanceEntry.entryType","entryType")}} برابر با `"mark"` است.

ورودی‌های این نوع معمولاً با فراخوانی {{domxref("Performance.mark","performance.mark()")}} برای افزودن یک {{domxref("DOMHighResTimeStamp")}} _نام‌گذاری شده_ (نشانه یا _mark_) به جدول زمانی عملکرد (performance timeline) مرورگر ایجاد می‌شوند. برای ایجاد یک نشانه عملکرد که به جدول زمانی عملکرد مرورگر اضافه نمی‌شود، از سازنده (constructor) استفاده کنید.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("PerformanceMark.PerformanceMark", "PerformanceMark()")}}
  - : یک شیء `PerformanceMark` جدید ایجاد می‌کند که به جدول زمانی عملکرد مرورگر اضافه نمی‌شود.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("PerformanceMark.detail")}}
  - : حاوی ابرداده‌های دلخواه درباره اندازه‌گیری (measure) است.

این رابط (interface) ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} با تعیین/محدود کردن آنها به صورت زیر گسترش می‌دهد:

- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}}
  - : مقدار `"mark"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}}
  - : نامی که هنگام ایجاد نشانه از طریق فراخوانی {{domxref("Performance.mark()","performance.mark()")}} به آن داده شده است را برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}}
  - : {{domxref("DOMHighResTimeStamp")}} مربوط به زمان فراخوانی {{domxref("Performance.mark()","performance.mark()")}} را برمی‌گرداند.
- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}}
  - : مقدار `0` را برمی‌گرداند. (یک نشانه _مدت زمان_ ندارد.)

## روش‌های نمونه (Instance methods)

این رابط هیچ روشی ندارد.

## مثال

مثال را در [استفاده از User Timing API](/en-US/docs/Web/API/Performance_API/User_timing) ببینید.

Chrome DevTools از `performance.mark()` و به طور خاص از ویژگی ساختاریافته `detail` به عنوان بخشی از API توسعه‌پذیری خود استفاده می‌کند که این موارد را در ردیابی‌های سفارشی در ردیابی‌های عملکرد (performance traces) نمایش می‌دهد. برای اطلاعات بیشتر و مثال‌ها، به مثال در صفحه [Performance: mark() method](/en-US/docs/Web/API/Performance/mark) و [مستندات API توسعه‌پذیری Chrome](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_the_user_timings_api) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [User Timing (Overview)](/en-US/docs/Web/API/Performance_API/User_timing)
- [Using the User Timing API](/en-US/docs/Web/API/Performance_API/User_timing)