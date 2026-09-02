---
title: InstallEvent
slug: Web/API/InstallEvent
page-type: web-api-interface
browser-compat: api.InstallEvent
---

{{APIRef("Service Workers API")}}

پارامتری که به تابع کنترل‌کننده رویداد {{DOMxRef("ServiceWorkerGlobalScope.install_event", "install")}} ارسال می‌شود. رابط `InstallEvent` نشان‌دهنده یک عمل نصب است که در {{domxref("ServiceWorkerGlobalScope")}} یک {{domxref("ServiceWorker")}} ارسال می‌شود. به عنوان فرزند {{domxref("ExtendableEvent")}}، تضمین می‌کند که رویدادهای عملکردی مانند {{domxref("FetchEvent")}} در طول نصب ارسال نشوند.

این رابط از رابط {{domxref("ExtendableEvent")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("InstallEvent.InstallEvent", "InstallEvent()")}}
  - : یک شیء `InstallEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("ExtendableEvent")}}، به ارث می‌برد._

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("ExtendableEvent")}}، به ارث می‌برد._

- {{domxref("InstallEvent.addRoutes()", "addRoutes()")}}
  - : یک یا چند مسیر ایستا مشخص می‌کند که قوانینی برای واکشی منابع مشخص شده تعریف می‌کنند که حتی قبل از راه‌اندازی service worker استفاده خواهند شد.

## نمونه‌ها

این قطعه کد از [نمونه پیش‌واکشی service worker](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/prefetch/service-worker.js) گرفته شده است (به [اجرای زنده پیش‌واکشی](https://googlechrome.github.io/samples/service-worker/prefetch/) مراجعه کنید). کد {{domxref("ExtendableEvent.waitUntil", "ExtendableEvent.waitUntil()")}} را در {{domxref("ServiceWorkerGlobalScope.install_event", "ServiceWorkerGlobalScope.oninstall")}} فراخوانی می‌کند و تا زمانی که promise ارسالی با موفقیت حل شود، کارگر {{domxref("ServiceWorkerRegistration.installing")}} را به‌عنوان نصب‌شده در نظر نمی‌گیرد. این promise زمانی حل می‌شود که همه منابع واکشی و ذخیره شده‌اند، یا در صورت بروز هر استثنایی.

قطعه کد همچنین یک روش خوب برای نسخه‌بندی کش‌های استفاده شده توسط service worker را نشان می‌دهد. اگرچه این مثال فقط یک کش دارد، می‌توانید از این رویکرد برای چندین کش استفاده کنید. کد یک شناسه کوتاه برای یک کش را به یک نام کش خاص و دارای نسخه نگاشت می‌کند.

> [!NOTE]
> عبارت‌های لاگ در Google Chrome از طریق رابط "Inspect" برای service worker مربوطه که از طریق chrome://serviceworker-internals قابل دسترسی است، قابل مشاهده هستند.

```js
const CACHE_VERSION = 1;
const CURRENT_CACHES = {
  prefetch: `prefetch-cache-v${CACHE_VERSION}`,
};

self.addEventListener("install", (event) => {
  const urlsToPrefetch = [
    "./static/pre_fetched.txt",
    "./static/pre_fetched.html",
    "https://www.chromium.org/_/rsrc/1302286216006/config/customLogo.gif",
  ];

  console.log(
    "Handling install event. Resources to pre-fetch:",
    urlsToPrefetch,
  );

  event.waitUntil(
    caches
      .open(CURRENT_CACHES["prefetch"])
      .then((cache) =>
        cache.addAll(
          urlsToPrefetch.map(
            (urlToPrefetch) => new Request(urlToPrefetch, { mode: "no-cors" }),
          ),
        ),
      )
      .then(() => {
        console.log("All resources have been fetched and cached.");
      })
      .catch((error) => {
        console.error("Pre-fetching failed:", error);
      }),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [رویداد `install`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/install_event)
- {{domxref("NotificationEvent")}}
- {{jsxref("Promise")}}
- [Fetch API](/en-US/docs/Web/API/Fetch_API)