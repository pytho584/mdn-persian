---
title: "Navigator: sendBeacon() method"
short-title: sendBeacon()
slug: Web/API/Navigator/sendBeacon
page-type: web-api-instance-method
browser-compat: api.Navigator.sendBeacon
---

{{APIRef("HTML DOM")}}

متد **`navigator.sendBeacon()`** به‌صورت {{glossary("Asynchronous", "ناهمزمان")}} یک درخواست [HTTP POST](/en-US/docs/Web/HTTP/Reference/Methods/POST) حاوی مقدار کمی داده را به یک سرور وب ارسال می‌کند.

این متد برای ارسال داده‌های تحلیلی (analytics) به سرور وب در نظر گرفته شده است و از برخی مشکلات روش‌های قدیمی ارسال داده‌های تحلیلی، مانند استفاده از {{domxref("XMLHttpRequest","XMLHttpRequest")}}، جلوگیری می‌کند.

> [!NOTE]
> برای موارد استفاده‌ای که نیاز به ارسال درخواست با متدهایی غیر از `POST` دارید، یا می‌خواهید ویژگی‌های درخواست را تغییر دهید، یا به پاسخ سرور نیاز دارید، به‌جای آن از متد [`fetch()`](/en-US/docs/Web/API/Window/fetch) با ویژگی [`keepalive`](/en-US/docs/Web/API/RequestInit#keepalive) تنظیم‌شده روی `true` استفاده کنید.

## نحو (Syntax)

```js-nolint
sendBeacon(url)
sendBeacon(url, data)
```

### پارامترها

- `url`
  - : آدرس URL که _داده_ را دریافت می‌کند. می‌تواند نسبی یا مطلق باشد.
- `data` {{Optional_inline}}
  - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}}، یک {{domxref("Blob")}}، یک رشته متنی (string literal) یا یک شیء، یک {{domxref("FormData")}} یا یک شیء {{domxref("URLSearchParams")}} حاوی داده‌هایی که قرار است ارسال شوند. اندازه کل داده‌های در صف‌گذاری‌شده به ۶۴ کیلوبایت (۶۵,۵۳۶ بایت) محدود است.

### مقدار بازگشتی

اگر {{glossary("user agent", "عامل کاربر")}} با موفقیت `data` را برای انتقال در صف قرار داده باشد، `true` برمی‌گرداند. در غیر این صورت، `false` برمی‌گرداند.

## توضیحات

این متد برای کدهای تحلیلی و تشخیصی (analytics and diagnostics) در نظر گرفته شده است تا داده‌ها را به یک سرور ارسال کنند.

یکی از مشکلات ارسال داده‌های تحلیلی این است که یک وب‌سایت اغلب می‌خواهد زمانی که کاربر کارش با صفحه تمام شده است، داده‌های تحلیلی را ارسال کند؛ برای مثال، وقتی کاربر به صفحه دیگری منتقل می‌شود. در این وضعیت، مرورگر ممکن است در آستانه تخلیه (unload) صفحه باشد و در آن صورت ممکن است تصمیم بگیرد درخواست‌های ناهمزمان {{domxref("XMLHttpRequest")}} را ارسال نکند.

در گذشته، صفحات وب سعی می‌کردند تخلیه صفحه را به اندازه کافی به تأخیر بیندازند تا داده‌ها ارسال شوند. برای این کار از راه‌حل‌های جایگزین مانند موارد زیر استفاده می‌کردند:

- ارسال داده با یک فراخوانی مسدودکننده و همزمان (synchronous) `XMLHttpRequest`.
- ایجاد یک عنصر {{HTMLElement("img")}} و تنظیم ویژگی `src` آن. اکثر عامل‌های کاربر، تخلیه صفحه را برای بارگذاری تصویر به تأخیر می‌اندازند.
- ایجاد یک حلقه بدون عملیات (no-op loop) برای چند ثانیه.

همه این روش‌ها تخلیه سند را مسدود می‌کنند که این امر ناوبری به صفحه بعدی را کند می‌کند. صفحه بعدی هیچ کاری نمی‌تواند برای جلوگیری از این مشکل انجام دهد، بنابراین صفحه جدید کند به نظر می‌رسد، حتی اگر این تقصیر صفحه قبلی باشد.

با متد `sendBeacon()`، داده‌ها به‌صورت ناهمزمان زمانی که عامل کاربر فرصت داشته باشد منتقل می‌شوند، بدون اینکه تخلیه صفحه یا ناوبری بعدی به تأخیر بیفتد. این یعنی:

- داده‌ها به‌طور قابل‌اعتمادی ارسال می‌شوند
- به‌صورت ناهمزمان ارسال می‌شوند
- تأثیری بر بارگذاری صفحه بعدی ندارند

داده به‌صورت یک درخواست [HTTP POST](/en-US/docs/Web/HTTP/Reference/Methods/POST) ارسال می‌شود.

با این حال، محدودیت این است که اندازه بار (payload) به حدود ۶۴ کیلوبایت محدود است. برای انتقال داده‌های حجیم‌تر، به‌جای آن از `fetch()` استفاده کنید.

### ارسال داده‌های تحلیلی در پایان یک نشست

وب‌سایت‌ها اغلب می‌خواهند زمانی که کاربر کارش با صفحه تمام شده است، داده‌های تحلیلی یا تشخیصی را به سرور ارسال کنند. مطمئن‌ترین راه برای انجام این کار، ارسال داده در رویداد [`visibilitychange`](/en-US/docs/Web/API/Document/visibilitychange_event) است:

```js
document.addEventListener("visibilitychange", () => {
  if (document.visibilityState === "hidden") {
    navigator.sendBeacon("/log", analyticsData);
  }
});
```

#### اجتناب از unload و beforeunload

در گذشته، بسیاری از وب‌سایت‌ها از رویدادهای [`unload`](/en-US/docs/Web/API/Window/unload_event) یا [`beforeunload`](/en-US/docs/Web/API/Window/beforeunload_event) برای ارسال داده‌های تحلیلی در پایان یک نشست استفاده می‌کردند. با این حال، این کار بسیار غیرقابل‌اعتماد است. در بسیاری از موقعیت‌ها، به‌ویژه در دستگاه‌های موبایل، مرورگر رویدادهای `unload`، `beforeunload` یا `pagehide` را فعال نمی‌کند. برای مثال، این رویدادها در شرایط زیر فعال نمی‌شوند:

1. کاربر صفحه را بارگذاری می‌کند و با آن تعامل دارد.
2. وقتی کارش تمام می‌شود، به‌جای بستن تب، به یک برنامه دیگر سوئیچ می‌کند.
3. بعداً، با استفاده از مدیر برنامه‌های تلفن، برنامه مرورگر را می‌بندد.

علاوه بر این، رویداد `unload` با حافظه نهان بازگشت/رفتن به جلو ([bfcache](https://web.dev/articles/bfcache)) که در مرورگرهای مدرن پیاده‌سازی شده است، سازگار نیست. برخی مرورگرها، مانند فایرفاکس، با این ناسازگاری به این صورت برخورد می‌کنند که اگر صفحات شامل کنترل‌کننده‌های `unload` باشند، آن صفحات را از bfcache حذف می‌کنند و در نتیجه عملکرد را تحت تأثیر قرار می‌دهند. برخی دیگر، مانند سافاری و کروم در اندروید، به این صورت برخورد می‌کنند که وقتی کاربر در همان تب به صفحه دیگری منتقل می‌شود، رویداد `unload` را فعال نمی‌کنند.

فایرفاکس همچنین اگر صفحات شامل کنترل‌کننده‌های `beforeunload` باشند، آن صفحات را از bfcache حذف می‌کند.

#### استفاده از pagehide به عنوان راه‌حل جایگزین

برای پشتیبانی از مرورگرهایی که `visibilitychange` را پیاده‌سازی نمی‌کنند، از رویداد [`pagehide`](/en-US/docs/Web/API/Window/pagehide_event) استفاده کنید. مانند `beforeunload` و `unload`، این رویداد نیز به‌طور قابل‌اعتمادی فعال نمی‌شود، به‌ویژه در موبایل. با این حال، با bfcache سازگار است.

## مثال‌ها

مثال زیر یک کنترل‌کننده برای رویداد {{domxref("document.visibilitychange_event", "visibilitychange")}} مشخص می‌کند. کنترل‌کننده برای ارسال داده‌های تحلیلی، `sendBeacon()` را فراخوانی می‌کند.

```js
document.addEventListener("visibilitychange", () => {
  if (document.visibilityState === "hidden") {
    navigator.sendBeacon("/log", analyticsData);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد [`visibilitychange`](/en-US/docs/Web/API/Document/visibilitychange_event).
- صفحه نمای کلی {{domxref("Beacon_API","Beacon API", "", "true")}}.
- [Don't lose user and app state, use Page Visibility](https://www.igvita.com/2015/11/20/dont-lose-user-and-app-state-use-page-visibility/) به‌طور مفصل توضیح می‌دهد که چرا باید از `visibilitychange` استفاده کنید، نه `beforeunload`/`unload`.
- [Page Lifecycle API](https://developer.chrome.com/docs/web-platform/page-lifecycle-api#developer-recommendations-for-each-state) راهنمایی‌های بهترین روش‌ها را برای مدیریت رفتار چرخه حیات صفحه در برنامه‌های وب شما ارائه می‌دهد.
- [PageLifecycle.js](https://github.com/GoogleChromeLabs/page-lifecycle): یک کتابخانه جاوااسکریپت که با ناسازگاری‌های بین مرورگرها در رفتار چرخه حیات صفحه مقابله می‌کند.
- [Back/forward cache](https://web.dev/articles/bfcache) توضیح می‌دهد که حافظه نهان بازگشت/رفتن به جلو چیست و چه پیامدهایی برای رویدادهای مختلف چرخه حیات صفحه دارد.