---
title: ExtendableEvent
slug: Web/API/ExtendableEvent
page-type: web-api-interface
browser-compat: api.ExtendableEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

رابطهٔ **`ExtendableEvent`** طول عمر رویدادهای [`install`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/install_event) و [`activate`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/activate_event) را که به‌عنوان بخشی از چرخه‌ی حیات سرویس‌ورکر (service worker) در محدوده‌ی سراسری (global scope) ارسال می‌شوند، افزایش می‌دهد. این کار تضمین می‌کند که هیچ رویداد عملکردی (مانند {{domxref("FetchEvent")}}) تا زمانی که طرح‌های پایگاه داده ارتقا نیافته و ورودی‌های کش قدیمی حذف نشده‌اند، ارسال نشود.

اگر {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} خارج از کنترل‌کننده‌ی رویداد `ExtendableEvent` فراخوانی شود، مرورگر باید یک خطای `InvalidStateError` صادر کند؛ همچنین توجه داشته باشید که فراخوانی‌های متعدد روی هم جمع می‌شوند و پرامیس‌های حاصل به فهرست [پرامیس‌های افزایش طول عمر](https://w3c.github.io/ServiceWorker/#extendableevent-extend-lifetime-promises) اضافه می‌شوند.

این رابط از رابط {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

> [!NOTE]
> این رابط فقط زمانی در دسترس است که محدوده‌ی سراسری یک {{domxref("ServiceWorkerGlobalScope")}} باشد. زمانی که یک {{domxref("Window")}} یا محدوده‌ی نوع دیگری از worker باشد، در دسترس نیست.

## سازنده

- {{domxref("ExtendableEvent.ExtendableEvent()", "ExtendableEvent()")}}
  - : یک شیء جدید `ExtendableEvent` می‌سازد.

## ویژگی‌های نمونه

_ویژگی خاصی را پیاده‌سازی نمی‌کند، اما ویژگی‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

- {{domxref("ExtendableEvent.waitUntil", "ExtendableEvent.waitUntil()")}}
  - : طول عمر رویداد را افزایش می‌دهد. قرار است در [کنترل‌کننده‌ی رویداد](/en-US/docs/Web/API/Document_Object_Model/Events#registering_event_handlers) [`install`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/install_event) برای worker در حال نصب ({{domxref("ServiceWorkerRegistration.installing", "installing")}}) و در [کنترل‌کننده‌ی رویداد](/en-US/docs/Web/API/Document_Object_Model/Events#registering_event_handlers) [`activate`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/activate_event) برای worker فعال ({{domxref("ServiceWorkerRegistration.active", "active")}}) فراخوانی شود.

## مثال‌ها

این قطعه‌کد از [نمونه‌ی پیش‌واکشی سرویس‌ورکر](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/prefetch/service-worker.js) گرفته شده است (به [نمونه‌ی زنده‌ی پیش‌واکشی](https://googlechrome.github.io/samples/service-worker/prefetch/) مراجعه کنید). کد، {{domxref("ExtendableEvent.waitUntil()")}} را در {{domxref("ServiceWorkerGlobalScope.install_event", "oninstall")}} فراخوانی می‌کند و تا زمانی که پرامیس ارسال‌شده با موفقیت resolve شود، در نظر گرفتن worker در حال نصب ({{domxref("ServiceWorkerRegistration.installing")}}) را به تأخیر می‌اندازد. پرامیس زمانی resolve می‌شود که همه‌ی منابع واکشی و در کش ذخیره شده باشند، یا در صورت بروز هر استثنا رد شود.

این قطعه‌کد همچنین یک روش خوب برای نسخه‌بندی کش‌های استفاده‌شده توسط سرویس‌ورکر نشان می‌دهد. اگرچه در این مثال فقط یک کش وجود دارد، اما همین رویکرد برای چندین کش نیز قابل استفاده است. یک شناسه‌ی کوتاه برای یک کش به یک نام کش خاص و نسخه‌بندی‌شده نگاشت می‌شود.

> [!NOTE]
> در کروم، دستورات ثبت (logging) از طریق رابط «Inspect» برای سرویس‌ورکر مربوطه، که از طریق chrome://serviceworker-internals قابل دسترسی است، قابل مشاهده هستند.

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

> [!NOTE]
> هنگام واکشی منابع، اگر احتمال دارد منابع از سروری سرو شوند که از {{glossary("CORS")}} پشتیبانی نمی‌کند، استفاده از `{mode: 'no-cors'}` بسیار مهم است. در این مثال، [www.chromium.org](https://www.chromium.org/) از CORS پشتیبانی نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه‌ی سرویس‌ورکرها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از web workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)