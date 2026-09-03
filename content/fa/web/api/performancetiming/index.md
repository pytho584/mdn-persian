---
title: "PerformanceTiming"
---

---
title: PerformanceTiming
slug: Web/API/PerformanceTiming
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.PerformanceTiming
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

> [!WARNING]
> این رابط در [مشخصات سطح ۲ زمان‌بندی ناوبری](https://w3c.github.io/navigation-timing/#obsolete) منسوخ شده است. لطفاً به جای آن از رابط {{domxref("PerformanceNavigationTiming")}} استفاده کنید.

رابط **`PerformanceTiming`** یک رابط قدیمی است که برای سازگاری با نسخه‌های قبلی نگهداری می‌شود و شامل ویژگی‌هایی است که اطلاعات زمان‌بندی عملکرد را برای رویدادهای مختلف در هنگام بارگذاری و استفاده از صفحه فعلی ارائه می‌دهند. شما می‌توانید یک شیء `PerformanceTiming` که صفحه شما را توصیف می‌کند، با استفاده از ویژگی {{domxref("Performance.timing", "window.performance.timing")}} دریافت کنید.

## ویژگی‌های نمونه

_رابط `PerformanceTiming` هیچ ویژگی‌ای را به ارث نمی‌برد._

این ویژگی‌ها هر کدام زمان رسیدن به نقطه خاصی از فرآیند بارگذاری صفحه را توصیف می‌کنند. برخی از آنها با رویدادهای DOM هم‌خوانی دارند؛ برخی دیگر زمان انجام عملیات داخلی مرورگر را توصیف می‌کنند.

هر زمان به صورت یک عدد ارائه می‌شود که نشان‌دهنده لحظه مورد نظر به میلی‌ثانیه از شروع عصر یونیکس (UNIX epoch) است.

این ویژگی‌ها به ترتیب وقوع در طول فرآیند ناوبری فهرست شده‌اند.

- {{domxref("PerformanceTiming.navigationStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که اعلان پایان (prompt) رویداد unload در سند قبلی در همان بافت مرور (browsing context) پایان می‌یابد. اگر سند قبلی وجود نداشته باشد، این مقدار همان `PerformanceTiming.fetchStart` خواهد بود.
- {{domxref("PerformanceTiming.unloadEventStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که رویداد {{domxref("Window/unload_event", "unload")}} پرتاب شده است، که نشان‌دهنده زمان شروع تخلیه سند قبلی در پنجره است. اگر سند قبلی وجود نداشته باشد، یا اگر سند قبلی یا یکی از تغییر مسیرهای لازم (redirects) از همان مبدأ (same origin) نباشد، مقدار بازگشتی `0` است.
- {{domxref("PerformanceTiming.unloadEventEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مدیریت‌کننده رویداد {{domxref("Window/unload_event", "unload")}} به پایان می‌رسد. اگر سند قبلی وجود نداشته باشد، یا اگر سند قبلی یا یکی از تغییر مسیرهای لازم از همان مبدأ نباشد، مقدار بازگشتی `0` است.
- {{domxref("PerformanceTiming.redirectStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که اولین تغییر مسیر HTTP شروع می‌شود. اگر هیچ تغییر مسیری وجود نداشته باشد، یا اگر یکی از تغییر مسیرها از همان مبدأ نباشد، مقدار بازگشتی `0` است.
- {{domxref("PerformanceTiming.redirectEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که آخرین تغییر مسیر HTTP تکمیل می‌شود، یعنی زمانی که آخرین بایت پاسخ HTTP دریافت شده است. اگر هیچ تغییر مسیری وجود نداشته باشد، یا اگر یکی از تغییر مسیرها از همان مبدأ نباشد، مقدار بازگشتی `0` است.
- {{domxref("PerformanceTiming.fetchStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مرورگر آماده است تا سند را با استفاده از یک درخواست HTTP دریافت کند. این لحظه _قبل از_ بررسی هر کش برنامه (application cache) است.
- {{domxref("PerformanceTiming.domainLookupStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که جستجوی دامنه (domain lookup) شروع می‌شود. اگر از یک اتصال پایدار (persistent connection) استفاده شود، یا اطلاعات در کش یا یک منبع محلی ذخیره شده باشد، مقدار همان `PerformanceTiming.fetchStart` خواهد بود.
- {{domxref("PerformanceTiming.domainLookupEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که جستجوی دامنه به پایان می‌رسد. اگر از یک اتصال پایدار استفاده شود، یا اطلاعات در کش یا یک منبع محلی ذخیره شده باشد، مقدار همان `PerformanceTiming.fetchStart` خواهد بود.
- {{domxref("PerformanceTiming.connectStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که درخواست باز کردن یک اتصال به شبکه ارسال می‌شود. اگر لایه انتقال خطایی گزارش کند و برقراری اتصال دوباره شروع شود، زمان شروع آخرین برقراری اتصال داده می‌شود. اگر از یک اتصال پایدار استفاده شود، مقدار همان `PerformanceTiming.fetchStart` خواهد بود.
- {{domxref("PerformanceTiming.connectEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که اتصال به شبکه باز می‌شود. اگر لایه انتقال خطایی گزارش کند و برقراری اتصال دوباره شروع شود، زمان پایان آخرین برقراری اتصال داده می‌شود. اگر از یک اتصال پایدار استفاده شود، مقدار همان `PerformanceTiming.fetchStart` خواهد بود. یک اتصال زمانی باز در نظر گرفته می‌شود که تمام دست‌دهی اتصال امن (secure connection handshake) یا احراز هویت SOCKS خاتمه یابد.
- {{domxref("PerformanceTiming.secureConnectionStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که دست‌دهی اتصال امن شروع می‌شود. اگر چنین اتصالی درخواست نشده باشد، مقدار `0` برمی‌گرداند.
- {{domxref("PerformanceTiming.requestStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مرورگر درخواست دریافت سند واقعی را از سرور یا از کش ارسال کرده است. اگر لایه انتقال پس از شروع درخواست دچار خطا شود و اتصال دوباره برقرار شود، این ویژگی به زمان مربوط به درخواست جدید تنظیم می‌شود.
- {{domxref("PerformanceTiming.responseStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مرورگر اولین بایت پاسخ را از سرور، از کش یا از یک منبع محلی دریافت کرده است.
- {{domxref("PerformanceTiming.responseEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مرورگر آخرین بایت پاسخ را دریافت کرده است، یا اگر زودتر اتفاق بیفتد، زمانی که اتصال بسته شده است، از سرور، کش یا یک منبع محلی.
- {{domxref("PerformanceTiming.domLoading")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که تجزیه‌گر (parser) کار خود را شروع می‌کند، یعنی زمانی که {{domxref("Document.readyState")}} آن به `'loading'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} پرتاب می‌شود.
- {{domxref("PerformanceTiming.domInteractive")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که تجزیه‌گر کار خود را بر روی سند اصلی به پایان می‌رساند، یعنی زمانی که {{domxref("Document.readyState")}} آن به `'interactive'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} پرتاب می‌شود.
- {{domxref("PerformanceTiming.domContentLoadedEventStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : درست قبل از اینکه تجزیه‌گر رویداد {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}} را ارسال کند، یعنی درست بعد از اجرای تمام اسکریپت‌هایی که باید بلافاصله پس از تجزیه اجرا شوند.
- {{domxref("PerformanceTiming.domContentLoadedEventEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : درست بعد از اجرای تمام اسکریپت‌هایی که باید در اسرع وقت اجرا شوند، به ترتیب یا بدون ترتیب.
- {{domxref("PerformanceTiming.domComplete")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که تجزیه‌گر کار خود را بر روی سند اصلی به پایان می‌رساند، یعنی زمانی که {{domxref("Document.readyState")}} آن به `'complete'` تغییر می‌کند و رویداد متناظر {{domxref("Document/readystatechange_event", "readystatechange")}} پرتاب می‌شود.
- {{domxref("PerformanceTiming.loadEventStart")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که رویداد {{domxref("Window/load_event", "load")}} برای سند فعلی ارسال شده است. اگر این رویداد هنوز ارسال نشده باشد، مقدار `0` برمی‌گرداند.
- {{domxref("PerformanceTiming.loadEventEnd")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : زمانی که مدیریت‌کننده رویداد {{domxref("Window/load_event", "load")}} به پایان رسیده است، یعنی زمانی که رویداد load تکمیل می‌شود. اگر این رویداد هنوز ارسال نشده باشد، یا هنوز تکمیل نشده باشد، مقدار `0` برمی‌گرداند.

## روش‌های نمونه

_رابط `PerformanceTiming` هیچ روشی را به ارث نمی‌برد._

- {{domxref("PerformanceTiming.toJSON()")}} {{Deprecated_Inline}}
  - : یک [شیء JSON](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) برمی‌گرداند که این شیء `PerformanceTiming` را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("Performance.timing")}} که چنین شیئی را ایجاد می‌کند.
- {{domxref("PerformanceNavigationTiming")}} (بخشی از Navigation Timing Level 2) که جایگزین این API شده است.