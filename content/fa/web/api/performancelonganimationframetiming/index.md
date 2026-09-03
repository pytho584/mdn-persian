---
title: "PerformanceLongAnimationFrameTiming"
slug: Web/API/PerformanceLongAnimationFrameTiming
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PerformanceLongAnimationFrameTiming
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

رابط **`PerformanceLongAnimationFrameTiming`** در API فریم‌های انیمیشن طولانی (Long Animation Frames API) مشخص شده است و معیارهایی را در مورد فریم‌های انیمیشن طولانی (LoAFs) که رندرینگ را اشغال کرده و اجرای سایر وظایف را مسدود می‌کنند، فراهم می‌کند.

## توضیحات

فریم‌های انیمیشن طولانی (LoAFs) به‌روزرسانی‌های رندرینگی هستند که بیش از ۵۰ میلی‌ثانیه به تأخیر می‌افتند. LoAFs می‌توانند منجر به به‌روزرسانی‌های کند رابط کاربری (UI) شوند، کنترل‌ها را غیرفعال نشان دهند و باعث ایجاد افکت‌های انیمیشنی و اسکرول‌های [لرزان](/en-US/docs/Glossary/Jank) (غیر روان) شوند. این موضوع اغلب باعث نارضایتی کاربر می‌شود.

رابط `PerformanceLongAnimationFrameTiming` مجموعه‌ای دقیق از اطلاعات زیر را در مورد LoAFs فراهم می‌کند که به توسعه‌دهندگان امکان می‌دهد علل ریشه‌ای آن‌ها را محدود کنند:

- مجموعه‌ای دقیق از برچسب‌های زمانی برای هر LoAF.
- اطلاعات دقیق در مورد هر اسکریپتی که در ایجاد LoAF نقش داشته است، از طریق ویژگی {{domxref("PerformanceLongAnimationFrameTiming.scripts")}}. این ویژگی آرایه‌ای از اشیاء {{domxref("PerformanceScriptTiming")}} را برمی‌گرداند، یکی برای هر اسکریپت.

`PerformanceLongAnimationFrameTiming` از {{domxref("PerformanceEntry")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط مستقیماً ویژگی‌های زیر را تعریف می‌کند:

- {{domxref("PerformanceLongAnimationFrameTiming.blockingDuration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که نشان‌دهنده کل زمان (بر حسب میلی‌ثانیه) است که نخ اصلی از پاسخ به وظایف با اولویت بالا، مانند ورودی کاربر، مسدود شده است. این مقدار با در نظر گرفتن تمام [وظایف طولانی](/en-US/docs/Web/API/PerformanceLongTaskTiming#description) درون LoAF که `duration` آن‌ها بیش از `50ms` است، کم کردن `50ms` از هر کدام، اضافه کردن زمان رندرینگ به زمان طولانی‌ترین وظیفه، و جمع نتایج محاسبه می‌شود.
- {{domxref("PerformanceLongAnimationFrameTiming.firstUIEventTimestamp")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان اولین رویداد UI — مانند یک رویداد ماوس یا صفحه‌کلید — را که در طول فریم انیمیشن جاری در صف قرار گرفته است، نشان می‌دهد.
- {{domxref("PerformanceLongAnimationFrameTiming.paintTime")}} {{experimental_inline}}
  - : {{domxref("DOMHighResTimeStamp","برچسب زمانی")}} را برمی‌گرداند که فاز رندرینگ به پایان رسیده و فریم انیمیشن شروع شده است.
- {{domxref("PerformanceLongAnimationFrameTiming.presentationTime")}} {{experimental_inline}}
  - : {{domxref("DOMHighResTimeStamp","برچسب زمانی")}} را برمی‌گرداند که به‌روزرسانی UI در واقع روی صفحه نمایش داده شده است.
- {{domxref("PerformanceLongAnimationFrameTiming.renderStart")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان شروع چرخه رندرینگ را نشان می‌دهد، که شامل بازخوانی‌های {{domxref("Window.requestAnimationFrame()")}}، محاسبات استایل و طرح‌بندی، بازخوانی‌های {{domxref("ResizeObserver")}}، و بازخوانی‌های {{domxref("IntersectionObserver")}} می‌شود.
- {{domxref("PerformanceLongAnimationFrameTiming.scripts")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از نمونه‌های {{domxref("PerformanceScriptTiming")}} را برمی‌گرداند.
- {{domxref("PerformanceLongAnimationFrameTiming.styleAndLayoutStart")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که آغاز دوره زمانی صرف‌شده در محاسبات استایل و طرح‌بندی برای فریم انیمیشن جاری را نشان می‌دهد.

همچنین ویژگی‌های زیر از {{domxref("PerformanceEntry")}} را گسترش می‌دهد و آن‌ها را مطابق با توضیحات زیر محدود و واجد شرایط می‌کند:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که نشان‌دهنده زمان (بر حسب میلی‌ثانیه) صرف‌شده برای پردازش کامل LoAF است.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نوع ورودی را برمی‌گرداند که همیشه `"long-animation-frame"` است.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : نام ورودی را برمی‌گرداند که همیشه `"long-animation-frame"` است.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان شروع فریم انیمیشن را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("PerformanceLongAnimationFrameTiming.toJSON()")}} {{Experimental_Inline}}
  - : یک نمایش JSON از شیء `PerformanceLongAnimationFrameTiming` را برمی‌گرداند.

## مثال‌ها

برای مثال‌های مربوط به API فریم‌های انیمیشن طولانی، به [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing)
- {{domxref("PerformanceScriptTiming")}}