---
title: "FetchEvent: respondWith() method"
short-title: respondWith()
slug: Web/API/FetchEvent/respondWith
page-type: web-api-instance-method
browser-compat: api.FetchEvent.respondWith
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

روش **`respondWith()`** از {{domxref("FetchEvent")}} از رفتار پیش‌فرض مرورگر در هنگام واکشی جلوگیری می‌کند و به شما اجازه می‌دهد خودتان یک promise برای یک {{domxref("Response")}} ارائه دهید.

در بیشتر موارد، می‌توانید هر پاسخی که دریافت‌کننده آن را درک می‌کند ارائه دهید. برای مثال، اگر یک {{HTMLElement('img')}} درخواست را آغاز کند، بدنه پاسخ باید شامل داده‌های تصویری باشد. به دلایل امنیتی، چند قانون کلی وجود دارد:

- فقط زمانی می‌توانید اشیاء {{domxref("Response")}} از {{domxref("Response.type", "نوع")}} `"opaque"` برگردانید که {{domxref("request.mode", "mode")}} شیء {{domxref("fetchEvent.request")}} برابر `"no-cors"` باشد. این کار از نشت داده‌های خصوصی جلوگیری می‌کند.
- فقط زمانی می‌توانید اشیاء {{domxref("Response")}} از {{domxref("Response.type", "نوع")}} `"opaqueredirect"` برگردانید که {{domxref("request.mode", "mode")}} شیء {{domxref("fetchEvent.request")}} برابر `"manual"` باشد.
- نمی‌توانید اشیاء {{domxref("Response")}} از {{domxref("Response.type", "نوع")}} `"cors"` برگردانید اگر {{domxref("request.mode", "mode")}} شیء {{domxref("fetchEvent.request")}} برابر `"same-origin"` باشد.

## Syntax

```js-nolint
respondWith(response)
```

### پارامترها

- `response`
  - : یک {{domxref("Response")}} یا یک {{jsxref("Promise")}} که به یک `Response` تبدیل می‌شود. در غیر این صورت، یک خطای شبکه به Fetch برگردانده می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NetworkError` {{domxref("DOMException")}}
  - : در صورت بروز خطای شبکه در ترکیب‌های خاصی از مقادیر {{domxref("Request.mode","FetchEvent.request.mode")}} و {{domxref("Response.type")}}، همانطور که در «قوانین کلی» بالا اشاره شد، برگردانده می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورت عدم ارسال رویداد یا فراخوانی قبلی `respondWith()` برگردانده می‌شود.

## توضیحات

### تعیین URL نهایی یک منبع

از Firefox 59 به بعد، هنگامی که یک service worker یک {{domxref("Response")}} را به `FetchEvent.respondWith()` ارائه می‌دهد، مقدار {{domxref("Response.url")}} به عنوان URL نهایی تفکیک‌شده به درخواست شبکه رهگیری‌شده منتقل می‌شود. اگر مقدار {{domxref("Response.url")}} رشته خالی باشد، آنگاه {{domxref("Request.url","FetchEvent.request.url")}} به عنوان URL نهایی استفاده می‌شود.

در گذشته، {{domxref("Request.url","FetchEvent.request.url")}} در همه موارد به عنوان URL نهایی استفاده می‌شد. {{domxref("Response.url")}} ارائه‌شده عملاً نادیده گرفته می‌شد.

این بدان معناست که، برای مثال، اگر یک service worker یک stylesheet یا اسکریپت worker را رهگیری کند، آنگاه {{domxref("Response.url")}} ارائه‌شده برای تفکیک هر بارگذاری زیرمنبع نسبی {{cssxref("@import")}} یا {{domxref("WorkerGlobalScope.importScripts()","importScripts()")}} استفاده خواهد شد ([باگ Firefox 1222008](https://bugzil.la/1222008)).

برای بیشتر انواع درخواست‌های شبکه، این تغییر تأثیری ندارد زیرا نمی‌توانید URL نهایی را مشاهده کنید. با این حال، مواردی وجود دارد که در آنها این تغییر مهم است:

- اگر یک {{domxref("Window/fetch", "fetch()")}} رهگیری شود، می‌توانید URL نهایی را در {{domxref("Response.url")}} نتیجه مشاهده کنید.
- اگر یک اسکریپت [worker](/en-US/docs/Web/API/Web_Workers_API) رهگیری شود، URL نهایی برای تنظیم [`self.location`](/en-US/docs/Web/API/WorkerGlobalScope/location) و به عنوان URL پایه برای URLهای نسبی در اسکریپت worker استفاده می‌شود.
- اگر یک stylesheet رهگیری شود، URL نهایی به عنوان URL پایه برای تفکیک بارگذاری‌های نسبی {{cssxref("@import")}} استفاده می‌شود.

توجه داشته باشید که درخواست‌های ناوبری برای {{domxref("Window","Windows")}} و {{domxref("HTMLIFrameElement","iframes")}} از URL نهایی استفاده نمی‌کنند. روشی که مشخصات HTML برای مدیریت تغییرمسیرها در ناوبری استفاده می‌کند، در نهایت از URL درخواست برای {{domxref("Window.location")}} حاصل استفاده می‌کند. این بدان معناست که سایت‌ها می‌توانند در حالت آفلاین یک نمای «جایگزین» از یک صفحه وب ارائه دهند بدون اینکه URL قابل مشاهده برای کاربر تغییر کند.

## مثال‌ها

این رویداد fetch سعی می‌کند پاسخی را از API cache برگرداند و در غیر این صورت به شبکه بازمی‌گردد.

```js
addEventListener("fetch", (event) => {
  // Prevent the default, and handle the request ourselves.
  event.respondWith(
    (async () => {
      // Try to get the response from a cache.
      const cachedResponse = await caches.match(event.request);
      // Return it if we found one.
      if (cachedResponse) return cachedResponse;
      // If we didn't find a match in the cache, use the network.
      return fetch(event.request);
    })(),
  );
});
```

> [!NOTE]
> {{domxref("CacheStorage.match()", "caches.match()")}} یک روش راحت است. عملکرد معادل آن فراخوانی {{domxref("cache.match()")}} بر روی هر cache (به ترتیب برگردانده‌شده توسط {{domxref("CacheStorage.keys()", "caches.keys()")}}) تا زمانی است که یک {{domxref("Response")}} برگردانده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [Fetch API](/en-US/docs/Web/API/Fetch_API)