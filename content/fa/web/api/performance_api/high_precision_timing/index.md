```
---
title: High precision timing
slug: Web/API/Performance_API/High_precision_timing
page-type: guide
---

{{DefaultAPISidebar("Performance API")}}

Performance API اندازه‌گیری‌هایی با دقت بالا را ممکن می‌سازد؛ اندازه‌گیری‌هایی که بر پایهٔ زمان با وضوح بالقوهٔ زیرمیلی‌ثانیه‌ای و یک ساعت یکنواخت و پایا (monotonic clock) هستند که تحت تأثیر انحراف یا تنظیم ساعت سیستم قرار نمی‌گیرد. برای معیارگذاری دقیق (benchmarking)، به تایمرهای با وضوح بالا نیاز است، نه به مهرهای زمانیِ کمتر دقیق و غیریکنواختِ {{jsxref("Date")}}.

این صفحه مروری بر این موضوع ارائه می‌دهد که زمان با دقت بالا در Performance API چگونه کار می‌کند و با مهرهای زمانی {{jsxref("Date")}} چه تفاوتی دارد.

## `DOMHighResTimeStamp`

زمان‌بندی با دقت بالا با استفاده از نوع {{domxref("DOMHighResTimeStamp")}} برای مقادیر زمان به‌دست می‌آید. واحد این مقادیر میلی‌ثانیه است و دقت آن‌ها باید تا ۵ میکروثانیه (µs) باشد. با این حال، اگر مرورگر نتواند مقدار زمانی با دقت ۵ میکروثانیه ارائه دهد، می‌تواند مقدار را به‌صورت میلی‌ثانیه‌ای که فقط تا یک میلی‌ثانیه دقیق است نمایش دهد. این شرایط ممکن است به دلیل محدودیت‌های سخت‌افزاری/نرم‌افزاری یا ملاحظات امنیتی و حریم خصوصی رخ دهد. برای اطلاعات بیشتر، بخش [دقت کاهش‌یافته](#reduced_precision) را در ادامه ببینید.

همه مهرهای زمانی در Performance API از نوع {{domxref("DOMHighResTimeStamp")}} استفاده می‌کنند. پیش‌تر، Performance API (و سایر Web APIها) از نوع `EpochTimeStamp` (که قبلاً با نام `DOMTimeStamp` شناخته می‌شد) استفاده می‌کردند. استفاده از این نوع‌ها اکنون توصیه نمی‌شود.

## `Performance.now()` در مقایسه با `Date.now()`

در جاوااسکریپت، {{jsxref("Date.now()")}} تعداد میلی‌ثانیه‌های سپری‌شده از [مبدأ زمان (epoch)](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date) تعریف می‌شود؛ مبدأی که به‌صورت نیمه‌شب آغاز ۱ ژانویه ۱۹۷۰، UTC تعریف شده است. از سوی دیگر، متد `performance.now()` نسبت به ویژگی {{domxref("Performance.timeOrigin")}} سنجیده می‌شود. برای اطلاعات بیشتر، [بخش مبدأهای زمانی](#time_origins) را در ادامه ببینید.

زمان‌های `Date` در جاوااسکریپت ممکن است دچار انحراف ساعت سیستم شده یا تحت تنظیمات ساعت قرار گیرند. این یعنی مقدار زمان ممکن است همیشه به‌صورت یکنواخت و افزایشی نباشد. هدف اصلی اشیاء `Date` نمایش اطلاعات تاریخ و زمان به کاربر است؛ بنابراین بسیاری از سیستم‌عامل‌ها یک برنامهٔ کمکی (daemon) اجرا می‌کنند که به‌طور منظم زمان را همگام‌سازی می‌کند. ممکن است ساعت چند بار در ساعت، چند میلی‌ثانیه تصحیح شود.

متد `performance.now()` (و سایر مقادیر `DOMHighResTimeStamp`) مقادیری زمانی یکنواخت و افزایشی فراهم می‌کند و تحت تأثیر تنظیم ساعت قرار نمی‌گیرد. این یعنی تضمین می‌شود مقادیر `DOMHighResTimeStamp` حداقل برابر با (و نه کمتر از) آخرین باری که مقدار را خوانده‌اید باشند.

```js
Date.now(); // 1678889977578
performance.now(); // 233936
```

برای اندازه‌گیری کارایی، محاسبهٔ نرخ فریم دقیق (FPS)، حلقه‌های انیمیشن و مانند این‌ها، به‌جای {{jsxref("Date.now()")}} جاوااسکریپت، از زمان با وضوح بالا و افزایشیِ یکنواختِ موجود در {{domxref("Performance.now()")}} استفاده کنید.

به‌طور خلاصه:

| -                        | {{domxref("Performance.now()")}}      | {{jsxref("Date.now()")}}          |
| ------------------------ | ------------------------------------- | --------------------------------- |
| وضوح                     | زیر میلی‌ثانیه                        | میلی‌ثانیه                          |
| مبدأ                     | {{domxref("Performance.timeOrigin")}} | Unix Epoch (۱ ژانویه ۱۹۷۰، UTC) |
| تأثیرپذیری از تنظیم ساعت | خیر                                  | بله                                |
| افزایش یکنواخت           | بله                                  | خیر                               |

## مبدأهای زمانی

Performance API از ویژگی {{domxref("Performance.timeOrigin")}} برای تعیین خط پایهٔ مهرهای زمانی مرتبط با کارایی استفاده می‌کند. همه زمان‌های `DOMHighResTimeStamp` نسبت به ویژگی `timeOrigin` سنجیده می‌شوند.

در بافتارهای Window، این مبدأ زمانی، زمان شروع ناوبری است. در بافتارهای {{domxref("Worker")}} و {{domxref("ServiceWorker")}}، مبدأ زمانی، زمانی است که Worker اجرا می‌شود.

در نسخهٔ پیشین مشخصات (Level 1)، متد `performance.now()` نسبت به ویژگی [`performance.timing.navigationStart`](/en-US/docs/Web/API/PerformanceTiming/navigationStart) در مشخصات Navigation Timing سنجیده می‌شد. اما این موضوع در نسخهٔ بعدی مشخصات (Level 2) تغییر کرد و اکنون `performance.now()` نسبت به {{domxref("Performance.timeOrigin")}} سنجیده می‌شود؛ این کار هنگام مقایسهٔ مهرهای زمانی در میان صفحات وب، خطر تغییر ساعت را از بین می‌برد.

```js
// Level 1 (clock change risks)
currentTime = performance.timing.navigationStart + performance.now();

// Level 2 (no clock change risks)
currentTime = performance.timeOrigin + performance.now();
```

### همگام‌سازی مبدأهای زمانی بین بافتارها

برای در نظر گرفتن مبدأهای زمانی متفاوت در بافتارهای window و worker، باید مهرهای زمانیِ حاصل از اسکریپت‌های worker را با کمک ویژگی `timeOrigin` انتقال دهید تا زمان‌بندی‌ها برای کل برنامه همگام شوند. برای کد نمونه جهت همگام‌سازی زمان، بخش مثال‌ها را در صفحهٔ {{domxref("Performance.timeOrigin")}} ببینید.

## دقت کاهش‌یافته

به‌منظور محافظت در برابر حملات زمان‌بندی (timing attacks) و [اثرانگشت (fingerprinting)](/en-US/docs/Glossary/Fingerprinting)، انواع `DOMHighResTimeStamp` بر اساس وضعیت ایزوله بودن سایت، با دقت کاهش‌یافته ارائه می‌شوند.

- وضوح در بافتارهای ایزوله: ۵ میکروثانیه
- وضوح در بافتارهای غیرایزوله: ۱۰۰ میکروثانیه

برای اعمال ایزوله‌سازی متقاطع-منشأ (cross-origin isolation) روی سایت خود، از هدرهای {{HTTPHeader("Cross-Origin-Opener-Policy")}} (COOP) و {{HTTPHeader("Cross-Origin-Embedder-Policy")}} (COEP) استفاده کنید:

```http
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
```

این هدرها تضمین می‌کنند که یک سند سطح بالا، گروه بافتار مرورگری را با اسناد متقاطع-منشأ به اشتراک نمی‌گذارد. {{HTTPHeader("Cross-Origin-Opener-Policy")}} سند شما را در سطح فرایند ایزوله می‌کند و اگر مهاجمان آن را در یک پنجرهٔ بازشو (popup) باز کرده باشند، به شیء سراسری شما دسترسی نخواهند داشت؛ در نتیجه مجموعه‌ای از حملات متقاطع-منشأ که با نام [XS-Leaks](https://github.com/xsleaks/xsleaks) شناخته می‌شوند، مسدود می‌شود.

## جستارهای وابسته

- {{domxref("DOMHighResTimeStamp")}}
- {{domxref("Performance.timeOrigin")}}
- {{domxref("Performance.now()")}} / {{jsxref("Date.now()")}}
```