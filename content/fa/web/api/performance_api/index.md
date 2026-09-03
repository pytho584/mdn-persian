---
title: Performance APIs
slug: Web/API/Performance_API
page-type: web-api-overview
spec-urls:
  - https://wicg.github.io/element-timing/
  - https://w3c.github.io/event-timing/
  - https://w3c.github.io/hr-time/
  - https://w3c.github.io/largest-contentful-paint/
  - https://wicg.github.io/layout-instability/
  - https://w3c.github.io/longtasks/
  - https://w3c.github.io/navigation-timing/
  - https://w3c.github.io/paint-timing/
  - https://w3c.github.io/performance-timeline/
  - https://w3c.github.io/resource-timing/
  - https://w3c.github.io/server-timing/
  - https://w3c.github.io/user-timing/
  - https://w3c.github.io/long-animation-frames/
  - https://wicg.github.io/performance-measure-memory/
  - https://html.spec.whatwg.org/multipage/interaction.html#the-visibilitystateentry-interface
  - https://html.spec.whatwg.org/multipage/nav-history-apis.html#the-notrestoredreasons-interface
---

{{DefaultAPISidebar("Performance API")}}{{AvailableInWorkers}}

Performance API مجموعه‌ای از استانداردهاست که برای اندازه‌گیری عملکرد برنامه‌های وب استفاده می‌شود.

## مفاهیم و کاربرد

برای اطمینان از سرعت برنامه‌های وب، اندازه‌گیری و تحلیل معیارهای مختلف عملکرد ضروری است. Performance API معیارهای داخلی مهمی را فراهم می‌کند و امکان افزودن اندازه‌گیری‌های سفارشی شما را به خط زمانی عملکرد مرورگر می‌دهد. خط زمانی عملکرد شامل برچسب‌های زمانی با دقت بالا است و می‌تواند در ابزارهای توسعه‌دهنده نمایش داده شود. همچنین می‌توانید داده‌های آن را به نقاط پایانی تحلیل ارسال کنید تا معیارهای عملکرد را در طول زمان ثبت کنید.

هر معیار عملکرد توسط یک {{domxref("PerformanceEntry")}} نمایش داده می‌شود. یک ورودی عملکرد دارای `name`، `duration`، `startTime` و `type` است. همه معیارهای عملکرد از رابط `PerformanceEntry` ارث‌بری کرده و آن را بیشتر مشخص می‌کنند.

بیشتر ورودی‌های عملکرد بدون نیاز به اقدام شما ثبت می‌شوند و سپس از طریق {{domxref("Performance.getEntries()")}} یا (ترجیحاً) از طریق {{domxref("PerformanceObserver")}} قابل دسترسی هستند. به عنوان مثال، ورودی‌های {{domxref("PerformanceEventTiming")}} برای رویدادهایی که بیش از یک آستانه مشخص طول می‌کشند ثبت می‌شوند. اما Performance API همچنین به شما امکان می‌دهد رویدادهای سفارشی خود را با استفاده از رابط‌های {{domxref("PerformanceMark")}} و {{domxref("PerformanceMeasure")}} تعریف و ثبت کنید.

رابط اصلی {{domxref("Performance")}} در هر دو حوزه سراسری {{domxref("Window.performance", "Window")}} و {{domxref("WorkerGlobalScope.performance", "Worker")}} در دسترس است و به شما امکان می‌دهد ورودی‌های عملکرد سفارشی اضافه کنید، ورودی‌های عملکرد را پاک کنید و ورودی‌های عملکرد را بازیابی کنید.

رابط {{domxref("PerformanceObserver")}} به شما امکان می‌دهد به انواع مختلف ورودی‌های عملکرد در حین ثبت آن‌ها گوش دهید.

برای اطلاعات مفهومی بیشتر، به [راهنماهای Performance API](#guides) در زیر مراجعه کنید.

![UML diagram of Performance APIs](diagram.svg)

## مرجع

رابط‌های زیر در Performance API وجود دارند:

- {{domxref("EventCounts")}}
  - : یک نقشه فقط‌خواندنی که توسط {{domxref("performance.eventCounts")}} بازگردانده می‌شود و شامل تعداد رویدادهای ارسال‌شده به‌ازای هر نوع رویداد است.
- {{domxref("LargestContentfulPaint")}}
  - : زمان رندر بزرگترین تصویر یا بلوک متنی قابل مشاهده در viewport را اندازه‌گیری می‌کند که از زمان شروع بارگذاری صفحه ثبت می‌شود.
- {{domxref("LayoutShift")}}
  - : بینش‌هایی در مورد پایداری چیدمان صفحات وب بر اساس جابجایی عناصر در صفحه ارائه می‌دهد.
- {{domxref("LayoutShiftAttribution")}}
  - : اطلاعات اشکال‌زدایی در مورد عناصری که جابجا شده‌اند ارائه می‌دهد.
- {{domxref("NotRestoredReasonDetails")}}
  - : یک دلیل واحد را نشان می‌دهد که چرا یک صفحه پیمایش‌شده از استفاده از حافظه نهان برگشت/جلو ({{Glossary("bfcache")}}) مسدود شده است.
- {{domxref("NotRestoredReasons")}}
  - : داده‌های گزارشی شامل دلایل مسدود شدن استفاده از حافظه نهان برگشت/جلو ({{Glossary("bfcache")}}) برای سند فعلی در هنگام پیمایش ارائه می‌دهد.
- {{domxref("Performance")}}
  - : رابط اصلی برای دسترسی به اندازه‌گیری‌های عملکرد. با استفاده از {{domxref("Window.performance")}} یا {{domxref("WorkerGlobalScope.performance")}} در زمینه‌های window و worker در دسترس است.
- {{domxref("PerformanceElementTiming")}}
  - : برچسب‌های زمانی رندر عناصر خاص را اندازه‌گیری می‌کند.
- {{domxref("PerformanceEntry")}}
  - : یک ورودی در خط زمانی عملکرد که یک معیار عملکرد واحد را در خود جای می‌دهد. همه معیارهای عملکرد از این رابط ارث‌بری می‌کنند.
- {{domxref("PerformanceEventTiming")}}
  - : تأخیر رویدادها و {{Glossary("Interaction to Next Paint")}} (INP) را اندازه‌گیری می‌کند.
- {{domxref("PerformanceLongAnimationFrameTiming")}}
  - : معیارهایی در مورد [فریم‌های انیمیشن طولانی (LoAFs)](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#what_is_a_long_animation_frame) که رندر را اشغال کرده و اجرای وظایف دیگر را مسدود می‌کنند، ارائه می‌دهد.
- {{domxref("PerformanceLongTaskTiming")}}
  - : معیارهایی در مورد [وظایف طولانی](/en-US/docs/Glossary/Long_task) که رندر را اشغال کرده و اجرای وظایف دیگر را مسدود می‌کنند، ارائه می‌دهد.
- {{domxref("PerformanceMark")}}
  - : نشانگر سفارشی برای ورودی خودتان در خط زمانی عملکرد.
- {{domxref("PerformanceMeasure")}}
  - : اندازه‌گیری زمانی سفارشی بین دو ورودی عملکرد.
- {{domxref("PerformanceNavigationTiming")}}
  - : رویدادهای پیمایش سند را اندازه‌گیری می‌کند، مانند مدت زمان بارگذاری یک سند.
- {{domxref("PerformanceObserver")}}
  - : به ورودی‌های عملکرد جدید در حین ثبت آن‌ها در خط زمانی عملکرد گوش می‌دهد.
- {{domxref("PerformanceObserverEntryList")}}
  - : فهرستی از ورودی‌هایی که در یک مشاهده‌گر عملکرد مشاهده شده‌اند.
- {{domxref("PerformancePaintTiming")}}
  - : عملیات رندر را در طول ساخت صفحه وب اندازه‌گیری می‌کند.
- {{domxref("PerformanceResourceTiming")}}
  - : معیارهای بارگذاری شبکه مانند زمان شروع و پایان تغییر مسیر، شروع واکشی، زمان شروع و پایان جستجوی DNS، زمان شروع و پایان پاسخ برای منابعی مانند تصاویر، اسکریپت‌ها، فراخوانی‌های fetch و غیره را اندازه‌گیری می‌کند.
- {{domxref("PerformanceScriptTiming")}}
  - : معیارهایی در مورد اسکریپت‌های منفرد که باعث [فریم‌های انیمیشن طولانی (LoAFs)](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing#what_is_a_long_animation_frame) می‌شوند، ارائه می‌دهد.
- {{domxref("PerformanceServerTiming")}}
  - : معیارهای سمت سرور را که با پاسخ در هدر HTTP {{HTTPHeader("Server-Timing")}} ارسال می‌شوند، نشان می‌دهد.
- {{domxref("TaskAttributionTiming")}}
  - : نوع وظیفه و ظرفی که مسئول وظیفه طولانی است را شناسایی می‌کند.
- {{domxref("VisibilityStateEntry")}}
  - : زمان تغییرات وضعیت دید صفحه را اندازه‌گیری می‌کند، یعنی زمانی که یک تب از پیش‌زمینه به پس‌زمینه تغییر می‌کند یا برعکس.

## راهنماها

راهنماهای زیر به شما در درک مفاهیم کلیدی Performance API کمک می‌کنند و نمای کلی از قابلیت‌های آن ارائه می‌دهند:

- [داده‌های عملکرد](/en-US/docs/Web/API/Performance_API/Performance_data): جمع‌آوری، دسترسی و کار با داده‌های عملکرد.
- [زمان‌بندی با دقت بالا](/en-US/docs/Web/API/Performance_API/High_precision_timing): اندازه‌گیری با زمان با دقت بالا و ساعت‌های یکنواخت.
- [زمان‌بندی منابع](/en-US/docs/Web/API/Performance_API/Resource_timing): اندازه‌گیری زمان‌بندی شبکه برای منابع واکشی‌شده، مانند تصاویر، CSS و جاوااسکریپت.
- [زمان‌بندی پیمایش](/en-US/docs/Web/API/Performance_API/Navigation_timing): اندازه‌گیری زمان‌بندی پیمایش یک سند.
- [زمان‌بندی کاربر](/en-US/docs/Web/API/Performance_API/User_timing): اندازه‌گیری و ثبت داده‌های عملکرد سفارشی برای برنامه شما.
- [زمان‌بندی سرور](/en-US/docs/Web/API/Performance_API/Server_timing): جمع‌آوری معیارهای سمت سرور.
- [زمان‌بندی فریم انیمیشن طولانی](/en-US/docs/Web/API/Performance_API/Long_animation_frame_timing): جمع‌آوری معیارهایی در مورد فریم‌های انیمیشن طولانی (LoAFs) و علل آن‌ها.
- [نظارت بر دلایل مسدود شدن bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons): گزارش در مورد اینکه چرا سند فعلی از استفاده از حافظه نهان برگشت/جلو ({{Glossary("bfcache")}}) مسدود شده است.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عملکرد وب](/en-US/docs/Web/Performance)
- [یادگیری: عملکرد وب](/en-US/docs/Learn_web_development/Extensions/Performance)