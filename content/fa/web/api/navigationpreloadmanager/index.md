---
title: "NavigationPreloadManager"
---

---
title: NavigationPreloadManager
slug: Web/API/NavigationPreloadManager
page-type: web-api-interface
browser-compat: api.NavigationPreloadManager
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

**`NavigationPreloadManager`** واسطهای در [Service Worker API](/en-US/docs/Web/API/Service_Worker_API) است که روشهایی را برای مدیریت بارگذاری از پیشِ منابع بهصورت موازی با راهاندازی سرویسورکر فراهم میکند.

در صورت پشتیبانی، یک شیء از این نوع توسط {{domxref("ServiceWorkerRegistration.navigationPreload")}} بازگردانده میشود.
نتیجهٔ یک درخواست واکشیِ از پیشبارگذاریشده با استفاده از پرامیسی که توسط {{domxref("FetchEvent.preloadResponse")}} بازگردانده میشود، انتظار کشیده میشود.

## روشهای نمونه

- {{domxref("NavigationPreloadManager.enable()")}}
  - : پیشبارگذاری ناوبری را فعال میکند و یک {{jsxref("Promise")}} بازمیگرداند که با {{jsxref('undefined')}} resolve میشود.
- {{domxref("NavigationPreloadManager.disable()")}}
  - : پیشبارگذاری ناوبری را غیرفعال میکند و یک {{jsxref("Promise")}} بازمیگرداند که با {{jsxref('undefined')}} resolve میشود.
- {{domxref("NavigationPreloadManager.setHeaderValue()")}}
  - : مقدار هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} را که در درخواستهای پیشبارگذاری ارسال میشود، تنظیم میکند و یک {{jsxref("Promise")}} خالی بازمیگرداند.
- {{domxref("NavigationPreloadManager.getState()")}}
  - : یک {{jsxref("Promise")}} بازمیگرداند که به یک شیء با ویژگیهایی resolve میشود که نشان میدهند آیا پیشبارگذاری فعال است و چه مقداری در هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} در درخواستهای پیشبارگذاری ارسال خواهد شد.

## توضیحات

سرویسورکرها رویدادهای {{domxref("Window/fetch", "fetch()")}} را از طرف یک وبسایت، برای صفحات درون یک محدودهٔ معین، مدیریت میکنند.
وقتی کاربر به صفحهای میرود که از سرویسورکر استفاده میکند، مرورگر سرویسورکر را راهاندازی میکند (اگر از قبل در حال اجرا نباشد)، سپس یک رویداد fetch به آن ارسال میکند و منتظر نتیجه میماند.
هنگام دریافت رویداد، سرویسورکر منبع را از کش برمیگرداند اگر موجود باشد، یا در غیر این صورت منبع را از سرور راه دور واکشی میکند (و یک نسخه برای درخواستهای آینده ذخیره میکند).

یک سرویسورکر نمیتواند رویدادهای مرورگر را پردازش کند تا زمانی که راهاندازی شود.
این امر اجتنابناپذیر است، اما معمولاً تأثیر زیادی ندارد.
سرویسورکرها اغلب از قبل شروع به کار کردهاند (آنها مدتی پس از پردازش درخواستهای دیگر فعال میمانند).
حتی اگر سرویسورکر مجبور باشد راهاندازی شود، در بسیاری از موارد ممکن است مقادیر را از کش برگرداند که بسیار سریع است.
اما در مواردی که سرویسورکر باید قبل از شروع به واکشی یک منبع راه دور راهاندازی شود، تأخیر میتواند قابل توجه باشد.

`NavigationPreloadManager` مکانیزمی را فراهم میکند که امکان واکشی منابع را بهصورت موازی با راهاندازی سرویسورکر میدهد، بهگونهای که تا زمانی که سرویسورکر بتواند درخواست fetch را از مرورگر پردازش کند، ممکن است منبع قبلاً بهطور کامل یا جزئی دانلود شده باشد.
این کار حالتی را که در آن سرویسورکر باید راهاندازی شود «بدتر از» حالتی که سرویسورکر از قبل شروع به کار کرده است نمیکند و در برخی موارد بهتر است.

مدیر پیشبارگذاری هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} را با درخواستهای پیشبارگذاری ارسال میکند و امکان سفارشیسازی پاسخها برای درخواستهای پیشبارگذاری را فراهم میکند.
برای مثال، ممکن است از این برای کاهش دادههای ارسالی به فقط بخشی از صفحهٔ اصلی، یا سفارشیسازی پاسخ بر اساس وضعیت ورود کاربر استفاده شود.

## مثالها

مثالهای اینجا از [سرعت بخشیدن به سرویسورکر با پیشبارگذاری ناوبری](https://web.dev/blog/navigation-preload) (developer.chrome.com) گرفته شدهاند.

### تشخیص ویژگی و فعالسازی پیشبارگذاری ناوبری

در زیر، پیشبارگذاری ناوبری را در دستگیرهٔ رویداد `activate` سرویسورکر فعال میکنیم، ابتدا با استفاده از {{domxref("ServiceWorkerRegistration.navigationPreload")}} بررسی میکنیم که آیا این ویژگی پشتیبانی میشود (این یا `NavigationPreloadManager` را برای سرویسورکر برمیگرداند یا اگر ویژگی پشتیبانی نشود، `undefined` را).

```js
addEventListener("activate", (event) => {
  event.waitUntil(
    (async () => {
      if (self.registration.navigationPreload) {
        // Enable navigation preloads!
        await self.registration.navigationPreload.enable();
      }
    })(),
  );
});
```

### استفاده از پاسخ از پیشبارگذاریشده

کد زیر یک دستگیرهٔ رویداد fetch سرویسورکر را نشان میدهد که از یک پاسخ از پیشبارگذاریشده ({{domxref("FetchEvent.preloadResponse")}}) استفاده میکند.

دستگیرهٔ رویداد `fetch` متد {{domxref("FetchEvent.respondWith", "FetchEvent.respondWith()")}} را فراخوانی میکند تا یک پرامیس را به صفحهٔ کنترلشده بازگرداند.
این پرامیس با منبع درخواستشده resolve میشود که ممکن است از کش، یک درخواست واکشیِ از پیشبارگذاریشده، یا یک درخواست شبکهٔ جدید باشد.

اگر یک درخواست URL منطبق در شیء {{domxref("Cache")}} وجود داشته باشد، کد یک پرامیس resolveشده برای واکشی پاسخ از کش برمیگرداند.
اگر هیچ تطابقی در کش یافت نشود، کد پاسخ از پیشبارگذاریشدهٔ resolveشده را برمیگرداند ({{domxref("FetchEvent.preloadResponse")}}).
اگر هیچ ورودی کش یا پاسخ از پیشبارگذاریشدهٔ مطابقی وجود نداشته باشد، کد یک عملیات fetch جدید از شبکه آغاز میکند و پرامیس (resolveنشده) را برای آن عملیات fetch برمیگرداند.

```js
addEventListener("fetch", (event) => {
  event.respondWith(
    (async () => {
      // Respond from the cache if we can
      const cachedResponse = await caches.match(event.request);
      if (cachedResponse) return cachedResponse;

      // Else, use the preloaded response, if it's there
      const response = await event.preloadResponse;
      if (response) return response;

      // Else try the network.
      return fetch(event.request);
    })(),
  );
});
```

### پاسخهای سفارشی

مرورگر هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} را با درخواستهای پیشبارگذاری ارسال میکند، با مقدار دستوری پیشفرض `true`.
این به سرورها امکان میدهد بین درخواستهای واکشی عادی و پیشبارگذاری تمایز قائل شوند و در صورت نیاز، پاسخهای متفاوتی در هر مورد ارسال کنند.

> [!NOTE]
> اگر پاسخ عملیات پیشبارگذاری و واکشی عادی میتواند متفاوت باشد، سرور باید `Vary: Service-Worker-Navigation-Preload` را تنظیم کند تا اطمینان حاصل شود که پاسخهای مختلف ذخیره میشوند.

مقدار هدر میتواند با استفاده از {{domxref("NavigationPreloadManager.setHeaderValue()")}} به هر رشتهٔ دیگری تغییر یابد تا زمینهٔ اضافی برای عملیات پیشواکشی فراهم شود.
برای مثال، میتوانید مقدار را به شناسهٔ آخرین منبع ذخیرهشدهٔ خود تنظیم کنید تا سرور هیچ منبعی را برنگرداند مگر اینکه واقعاً مورد نیاز باشد.
بهطور مشابه، میتوانید اطلاعات بازگرداندهشده را بر اساس وضعیت احراز هویت پیکربندی کنید، بهجای استفاده از کوکیها.

کد زیر نحوهٔ تنظیم مقدار دستور هدر را به متغیری به نام `newValue` نشان میدهد.

```js
navigator.serviceWorker.ready
  .then((registration) =>
    registration.navigationPreload.setHeaderValue(newValue),
  )
  .then(() => {
    console.log("Done!");
  });
```

[سرعت بخشیدن به سرویسورکر با پیشبارگذاری ناوبری > پاسخهای سفارشی برای پیشبارگذاریها](https://web.dev/blog/navigation-preload) مثال کاملتری از یک وبسایت ارائه میدهد که در آن پاسخ یک صفحهٔ مقاله از یک هدر و فوتر ذخیرهشده ساخته میشود، بهطوری که فقط محتوای مقاله برای یک پیشواکشی بازگردانده شود.

### دریافت وضعیت

میتوانید از {{domxref("NavigationPreloadManager.getState()")}} برای بررسی اینکه آیا پیشبارگذاری ناوبری فعال است و برای تعیین اینکه چه مقدار دستوری با هدر HTTP {{HTTPHeader("Service-Worker-Navigation-Preload")}} برای درخواستهای پیشبارگذاری ارسال میشود، استفاده کنید.

کد زیر نحوهٔ دریافت پرامیسی را نشان میدهد که به یک شیء `state` resolve میشود و نتیجه را ثبت میکند.

```js
navigator.serviceWorker.ready
  .then((registration) => registration.navigationPreload.getState())
  .then((state) => {
    console.log(state.enabled); // boolean
    console.log(state.headerValue); // string
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [سرعت بخشیدن به سرویسورکر با پیشبارگذاری ناوبری](https://web.dev/blog/navigation-preload) (developer.chrome.com)