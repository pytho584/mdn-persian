---
title: PerformanceScriptTiming
slug: Web/API/PerformanceScriptTiming
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PerformanceScriptTiming
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

رابط **`PerformanceScriptTiming`** در Long Animation Frames API تعریف شده است و معیارهایی را برای هر اسکریپتی که در ایجاد فریم‌های انیمیشن طولانی (LoAF) نقش دارد ارائه می‌کند.

## توضیحات

فریم‌های انیمیشن طولانی (LoAFها) به‌روزرسانی‌های رندری هستند که بیش از ۵۰ میلی‌ثانیه به تأخیر افتاده‌اند. LoAFها می‌توانند باعث به‌روزرسانی‌های کند رابط کاربری (UI) شوند، کنترلها را واکنش‌ناپذیر نشان دهند و جلوه‌های متحرک و اسکرول‌کردن را [پرش‌دار (غیرنرم)](/en-US/docs/Glossary/Jank) کنند. این وضعیت اغلب به ناامیدی کاربر می‌انجامد.

رابط `PerformanceScriptTiming` (نمونه‌های آن از طریق ویژگی {{domxref("PerformanceLongAnimationFrameTiming.scripts")}} در دسترس است) مجموعه اطلاعات دقیق زیر را درباره هر اسکریپتی که در LoAFها مشارکت دارد در اختیار توسعه‌دهندگان می‌گذارد تا بتوانند علت‌های ریشه‌ای را مشخص کنند:

- مجموعه‌ای دقیق از برچسب‌های زمانی برای هر اسکریپت.
- هویت و نوع فراخواننده (invoker)؛ یعنی قابلیتی که با فراخوانده‌شدن، اسکریپت را اجرا کرد.
- اطلاعات دقیق درباره هر فایل منبع اسکریپت، ازجمله URL، نام تابع و موقعیت نویسه (کاراکتر) که در ایجاد LoAF نقش داشت.

`PerformanceScriptTiming` از {{domxref("PerformanceEntry")}} ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط ویژگی‌های {{domxref("PerformanceEntry")}} زیر را برای ورودی‌های Performance مربوط به فریم انیمیشن طولانی گسترش می‌دهد:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان سپری‌شده بر حسب میلی‌ثانیه بین شروع و پایان اجرای اسکریپت را نشان می‌دهد.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نوع ورودی را برمی‌گرداند که همیشه `"script"` است.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نام ورودی را برمی‌گرداند که همیشه `"script"` است.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان شروع اجرای اسکریپت را بر حسب میلی‌ثانیه نشان می‌دهد.

این رابط همچنین از ویژگی‌های زیر پشتیبانی می‌کند:

- {{domxref("PerformanceScriptTiming.executionStart")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان پایان کامپایل اسکریپت و شروع اجرای آن را نشان می‌دهد.
- {{domxref("PerformanceScriptTiming.forcedStyleAndLayoutDuration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که مجموع زمان صرف‌شده توسط اسکریپت برای پردازش چیدمان/استایل اجباری را بر حسب میلی‌ثانیه نشان می‌دهد. برای درک اینکه چه چیزی باعث این وضعیت می‌شود، به بخش [اجتناب از layout thrashing](https://web.dev/articles/avoid-large-complex-layouts-and-layout-thrashing#avoid_layout_thrashing) مراجعه کنید.
- {{domxref("PerformanceScriptTiming.invoker")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار رشته‌ای برمی‌گرداند که هویت قابلیتی را نشان می‌دهد که هنگام فراخوانده‌شدن، اسکریپت را اجرا کرد.
- {{domxref("PerformanceScriptTiming.invokerType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار رشته‌ای برمی‌گرداند که نوع قابلیتی را نشان می‌دهد که هنگام فراخوانده‌شدن، اسکریپت را اجرا کرد.
- {{domxref("PerformanceScriptTiming.pauseDuration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که مجموع زمان صرف‌شده توسط اسکریپت بر حسب میلی‌ثانیه برای «مکث» عملیات همگام (برای مثال، فراخوانی‌های {{domxref("Window.alert()")}} یا {{domxref("XMLHttpRequest")}}های همگام) را نشان می‌دهد.
- {{domxref("PerformanceScriptTiming.sourceCharPosition")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد برمی‌گرداند که موقعیت نویسه را در اسکریپتِ مربوط به قابلیتِ مشارکت‌کننده در LoAF نشان می‌دهد.
- {{domxref("PerformanceScriptTiming.sourceFunctionName")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که نام تابعِ مشارکت‌کننده در LoAF را نشان می‌دهد.
- {{domxref("PerformanceScriptTiming.sourceURL")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که URL اسکریپت را نشان می‌دهد.
- {{domxref("PerformanceScriptTiming.window")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به شیء {{domxref("Window")}} برمی‌گرداند که نمایانگر `window` ظرف (container) است؛ یعنی سند سطح بالا یا یک {{htmlelement("iframe")}} که اسکریپت ایجادکنندهٔ LoAF در آن اجرا شده است.
- {{domxref("PerformanceScriptTiming.windowAttribution")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار شمارشی برمی‌گرداند که رابطهٔ ظرف (سند سطح بالا یا یک {{htmlelement("iframe")}}) محل اجرای اسکریپتِ ایجادکنندهٔ LoAF را نسبت به `window`ای که سند فعلی را اجرا می‌کند توصیف می‌کند.

## متدهای نمونه

- {{domxref("PerformanceScriptTiming.toJSON()")}} {{Experimental_Inline}}
  - : یک نمایش JSON از شیء `PerformanceScriptTiming` برمی‌گرداند.

## نمونه‌ها

برای نمونه‌های مرتبط با Long Animation Frames API به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceLongAnimationFrameTiming")}}