---
title: PerformanceNavigationTiming
slug: Web/API/PerformanceNavigationTiming
page-type: web-api-interface
browser-compat: api.PerformanceNavigationTiming
---

{{APIRef("Performance API")}}

رابطه‌ی **`PerformanceNavigationTiming`** متدها و ویژگی‌هایی را برای ذخیره‌سازی و بازیابی معیارهای مربوط به رویدادهای ناوبری سند در مرورگر فراهم می‌کند. به عنوان مثال، می‌توان از این رابط برای تعیین مدت زمان لازم برای بارگذاری یا تخلیه‌ی یک سند استفاده کرد.

فقط سند فعلی در خط زمانی عملکرد قرار می‌گیرد، بنابراین تنها یک شیء `PerformanceNavigationTiming` در خط زمانی عملکرد وجود دارد. این رابط تمام ویژگی‌ها و متدهای {{domxref("PerformanceResourceTiming")}} و {{domxref("PerformanceEntry")}} را به ارث می‌برد.

{{InheritanceDiagram}}

نمودار زیر تمام ویژگی‌های برچسب زمانی تعریف‌شده در `PerformanceNavigationTiming` را نشان می‌دهد.

![نمودار برچسب‌های زمانی که ترتیب ثبت آن‌ها را برای واکشی یک سند فهرست می‌کند](https://mdn.github.io/shared-assets/images/diagrams/api/performance/timestamp-diagram.svg)

## ویژگی‌های نمونه

این رابط ویژگی‌های زیر از {{domxref('PerformanceEntry')}} را با محدودسازی و قید زیر گسترش می‌دهد:

- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}}
  - : مقدار `"navigation"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}}
  - : [نشانی وب سند](/en-US/docs/Web/API/Document/URL) را برمی‌گرداند.
    توجه داشته باشید که [قطعات متنی](/en-US/docs/Web/URI/Reference/Fragment/Text_fragments) و هر دستورالعمل قطعه‌ی دیگری از نشانی وب حذف می‌شوند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} با مقدار `0` برمی‌گرداند.
- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp","برچسب زمانی")}} برمی‌گرداند که تفاوت بین ویژگی‌های {{domxref("PerformanceNavigationTiming.loadEventEnd")}} و {{domxref("PerformanceEntry.startTime")}} است.

این رابط همچنین ویژگی‌های زیر از {{domxref('PerformanceResourceTiming')}} را با محدودسازی و قید زیر گسترش می‌دهد:

- {{domxref('PerformanceResourceTiming.initiatorType')}} {{ReadOnlyInline}}
  - : مقدار `"navigation"` را برمی‌گرداند.

این رابط همچنین از ویژگی‌های زیر پشتیبانی می‌کند:

- {{domxref('PerformanceNavigationTiming.activationStart')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده‌ی زمان بین شروع پیش‌رندر شدن یک سند و فعال‌سازی آن است.
- {{domxref('PerformanceNavigationTiming.confidence')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک شیء {{domxref("PerformanceTimingConfidence")}} حاوی اطلاعاتی که نشان می‌دهد آیا یک رکورد عملکرد منعکس‌کننده‌ی عملکرد معمولی برنامه است یا احتمالاً تحت تأثیر عوامل خارجی قرار دارد.
- {{domxref('PerformanceNavigationTiming.criticalCHRestart')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان وقوع راه‌اندازی مجدد اتصال را به دلیل عدم تطابق هدر پاسخ {{HTTPHeader("Critical-CH")}} نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.domComplete')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست قبل از تنظیم [`readyState`](/en-US/docs/Web/API/Document/readyState) سند به `"complete"` توسط عامل کاربر را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.domContentLoadedEventEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست پس از اتمام اجرای کنترل‌کننده‌ی رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.domContentLoadedEventStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست قبل از شروع اجرای کنترل‌کننده‌ی رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.domInteractive')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست قبل از تنظیم [`readyState`](/en-US/docs/Web/API/Document/readyState) سند به `"interactive"` توسط عامل کاربر را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.loadEventEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست پس از اتمام اجرای کنترل‌کننده‌ی رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.loadEventStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست قبل از شروع اجرای کنترل‌کننده‌ی رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.notRestoredReasons')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک شیء {{domxref("NotRestoredReasons")}} که داده‌های گزارشی درباره‌ی دلایل مسدود شدن سند فعلی از استفاده‌ی حافظه‌ی پنهان عقب/جلو ({{Glossary("bfcache")}}) در هنگام ناوبری فراهم می‌کند.
- {{domxref('PerformanceNavigationTiming.redirectCount')}} {{ReadOnlyInline}}
  - : عددی که تعداد تغییر مسیرها از آخرین ناوبری غیر تغییر مسیر در بافت مرور فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.type')}} {{ReadOnlyInline}}
  - : رشته‌ای که نوع ناوبری را نشان می‌دهد. یا `"navigate"`، یا `"reload"`، یا `"back_forward"`.
- {{domxref('PerformanceNavigationTiming.unloadEventEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست پس از اتمام اجرای کنترل‌کننده‌ی رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند فعلی را نشان می‌دهد.
- {{domxref('PerformanceNavigationTiming.unloadEventStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که زمان درست قبل از شروع اجرای کنترل‌کننده‌ی رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند فعلی را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("PerformanceNavigationTiming.toJSON()")}}
  - : یک نمایش JSON از شیء `PerformanceNavigationTiming` برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Performance.navigation")}}
- {{domxref("PerformanceNavigation")}}