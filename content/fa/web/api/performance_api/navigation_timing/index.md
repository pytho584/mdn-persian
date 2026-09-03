---
title: Navigation timing
slug: Web/API/Performance_API/Navigation_timing
page-type: web-api-overview
---

{{DefaultAPISidebar("Performance API")}}

«زمان‌بندی ناوبری» (Navigation Timing) بخشی از «Performance API» است و معیارهای مرتبط با پیمایش از یک صفحه به صفحهٔ دیگر را فراهم می‌کند. برای مثال، می‌توانید تعیین کنید بارگذاری یا تخلیهٔ یک سند چقدر طول می‌کشد، یا مدت‌زمان سپری‌شده تا پایان ساخت {{Glossary("DOM")}} و امکان تعامل با آن را ثبت کنید.

فقط سندِ فعلی لحاظ می‌شود، بنابراین معمولاً تنها یک شیء {{domxref("PerformanceNavigationTiming")}} برای مشاهده وجود دارد. این رابط، رابط {{domxref("PerformanceEntry")}} را با {{domxref("PerformanceEntry.entryType","entryType")}} برابر با `"navigation"` گسترش می‌دهد و همچنین از {{domxref("PerformanceResourceTiming")}} ارث می‌برد؛ بنابراین تمام مهرهای زمانی مربوط به فرایند واکشی سند نیز در دسترس هستند.

{{InheritanceDiagram("PerformanceNavigationTiming")}}

## مهرهای زمانی ناوبری

![Timestamp diagram listing timestamps in the order in which they are recorded for the fetching of a document](https://mdn.github.io/shared-assets/images/diagrams/api/performance/timestamp-diagram.svg)
شکل ۱: مهرهای زمانی ناوبری ([منبع](https://w3c.github.io/navigation-timing/#process)).

مهرهای زمانی ناوبری سند (علاوه بر آن‌هایی که از [Resource Timing](/en-US/docs/Web/API/Performance_API/Resource_timing) می‌آیند) عبارت‌اند از:

1. {{domxref("PerformanceEntry.startTime","startTime")}}: همیشه ۰.
2. {{domxref("PerformanceNavigationTiming.unloadEventStart","unloadEventStart")}}: (در صورت وجود سند قبلی) مهر زمانی بلافاصله پیش از شروع اجرای کنترل‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند فعلی.
3. {{domxref("PerformanceNavigationTiming.unloadEventEnd","unloadEventEnd")}}: (در صورت وجود سند قبلی) مهر زمانی بلافاصله پس از پایان اجرای کنترل‌کنندهٔ رویداد [`unload`](/en-US/docs/Web/API/Window/unload_event) سند فعلی.
4. {{domxref("PerformanceNavigationTiming.domInteractive","domInteractive")}}: مهر زمانی پایان ساخت DOM و زمانی که تعامل با آن از طریق JavaScript ممکن می‌شود.
5. {{domxref("PerformanceNavigationTiming.domContentLoadedEventStart","domContentLoadedEventStart")}}: مهر زمانی بلافاصله پیش از شروع اجرای کنترل‌کنندهٔ رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی.
6. {{domxref("PerformanceNavigationTiming.domContentLoadedEventEnd","domContentLoadedEventEnd")}}: مهر زمانی بلافاصله پس از پایان اجرای کنترل‌کنندهٔ رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) سند فعلی.
7. {{domxref("PerformanceNavigationTiming.domComplete","domComplete")}}: مهر زمانی پایان بارگذاری سند و همهٔ منابع فرعی.
8. {{domxref("PerformanceNavigationTiming.loadEventStart","loadEventStart")}}: مهر زمانی بلافاصله پیش از شروع اجرای کنترل‌کنندهٔ رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند فعلی.
9. {{domxref("PerformanceNavigationTiming.loadEventEnd","loadEventEnd")}}: مهر زمانی بلافاصله پس از پایان اجرای کنترل‌کنندهٔ رویداد [`load`](/en-US/docs/Web/API/Window/load_event) سند فعلی.

## اطمینان از زمان‌بندی عملکرد

ویژگی {{domxref("PerformanceNavigationTiming.confidence")}} یک شیء {{domxref("PerformanceTimingConfidence")}} برمی‌گرداند که حاوی اطلاعاتی است نشان می‌دهد آیا یک رکورد عملکرد، عملکرد معمولی برنامه را بازتاب می‌دهد یا احتمالاً تحت تأثیر عوامل خارجی قرار گرفته است.

برای مثال، اگر یک وب‌سایت پس از «شروع سرد» (cold start) مرورگر یا بازیابی نشست (session restore) بارگذاری شده باشد، ممکن است صفحات آن در نتیجه کندتر بارگذاری شوند. در چنین مواردی، یک `value` با درجه اطمینان `low` برای رکورد عملکرد مرتبط برگردانده می‌شود. از سوی دیگر، اگر مرورگر تشخیص دهد که رکورد عملکرد بازگردانده‌شده نمایانگر عملکرد معمولی برنامه است، مقدار اطمینان `high` برگردانده می‌شود.

این معیار اطمینان برای توسعه‌دهندگان مفید است تا تشخیص دهند آیا مشکل عملکرد یک نگرانی واقعی است یا یک مورد پرت (outlier) ناشی از عوامل خارجی. برای اطلاعات بیشتر به {{domxref("PerformanceTimingConfidence")}} مراجعه کنید.

## سایر ویژگی‌ها

رابط {{domxref("PerformanceNavigationTiming")}} ویژگی‌های بیشتری مانند {{domxref("PerformanceNavigationTiming.redirectCount","redirectCount")}} که تعداد ریدایرکت‌ها را برمی‌گرداند و {{domxref("PerformanceNavigationTiming.type","type")}} که نوع ناوبری را نشان می‌دهد، فراهم می‌کند.

## مثال

مهرهای زمانی `domContentLoadedEventEnd` و `domContentLoadedEventStart` را می‌توان برای اندازه‌گیری مدت‌زمان پردازش کنترل‌کنندهٔ رویداد [`DOMContentLoaded`](/en-US/docs/Web/API/Document/DOMContentLoaded_event) استفاده کرد.

این مثال از یک {{domxref("PerformanceObserver")}} استفاده می‌کند که دربارهٔ ورودی‌های عملکرد جدید `navigation` به محض ثبت‌شدن در خط زمانی عملکرد مرورگر، به فراخواننده اطلاع می‌دهد. در این مثال، از گزینهٔ `buffered` برای دسترسی به ورودی‌هایی استفاده می‌شود که پیش از ایجاد observer ثبت شده‌اند.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    const domContentLoadedTime =
      entry.domContentLoadedEventEnd - entry.domContentLoadedEventStart;
    console.log(
      `${entry.name}: DOMContentLoaded processing time: ${domContentLoadedTime}ms`,
    );
  });
});

observer.observe({ type: "navigation", buffered: true });
```

برای مثال‌های بیشتر، به صفحات ویژگی‌ها در مستندات مرجع {{domxref("PerformanceNavigationTiming")}} مراجعه کنید.

## همچنین ببینید

- {{domxref("PerformanceNavigationTiming")}}
- {{domxref("PerformanceResourceTiming")}}