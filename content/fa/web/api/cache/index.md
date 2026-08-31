---
title: "Cache"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache"
translated_by: "n8n + AI"
---

---
title: Cache
slug: Web/API/Cache
page-type: web-api-interface
browser-compat: api.Cache
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`Cache`** یک مکانیسم ذخیره‌سازی پایدار برای جفت‌های {{domxref("Request")}} / {{domxref("Response")}} فراهم می‌کند که در حافظه‌ای با عمر طولانی کش می‌شوند. مدت زمان زنده ماندن یک شیء `Cache` به مرورگر بستگی دارد، اما معمولاً اسکریپت‌های یک مبدأ واحد می‌توانند به وجود یک شیء `Cache` که قبلاً پر شده است اعتماد کنند. توجه داشته باشید که رابط `Cache` هم در scopeهای پنجره‌ای و هم در workerها در معرض دید قرار دارد. شما مجبور نیستید از آن در کنار service workerها استفاده کنید، اگرچه در مشخصات service worker تعریف شده است.

یک مبدأ می‌تواند چندین شیء `Cache` نام‌گذاری شده داشته باشد. شما مسئول پیاده‌سازی نحوه مدیریت به‌روزرسانی‌های `Cache` توسط اسکریپت خود (مثلاً در یک {{domxref("ServiceWorker")}}) هستید. موارد موجود در یک `Cache` به‌روزرسانی نمی‌شوند مگر اینکه صریحاً درخواست شوند؛ و منقضی نمی‌شوند مگر اینکه حذف شوند. از {{domxref("CacheStorage.open", "CacheStorage.open()")}} برای باز کردن یک شیء `Cache` نام‌گذاری شده خاص استفاده کنید و سپس هر یک از متدهای `Cache` را برای نگهداری `Cache` فراخوانی کنید.

همچنین شما مسئول پاکسازی دوره‌ای ورودی‌های کش هستید. هر مرورگر محدودیت سختی برای میزان فضای ذخیره‌سازی کش دارد که یک مبدأ معین می‌تواند استفاده کند. تخمین‌های استفاده از سهمیه `Cache` از طریق متد {{domxref("StorageManager.estimate()")}} در دسترس است. مرورگر بهترین تلاش خود را برای مدیریت فضای دیسک انجام می‌دهد، اما ممکن است ذخیره‌سازی `Cache` را برای یک مبدأ حذف کند. مرورگر معمولاً تمام داده‌های یک مبدأ را حذف می‌کند یا هیچ‌کدام را. حتماً کش‌ها را با نام نسخه‌بندی کنید و فقط از نسخه‌ای از اسکریپت که می‌تواند با خیال راحت روی آنها کار کند از کش‌ها استفاده کنید. برای اطلاعات بیشتر به [حذف کش‌های قدیمی](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers#deleting_old_caches) مراجعه کنید.

> [!NOTE]
> الگوریتم تطبیق کلید به [header VARY](https://www.fastly.com/blog/best-practices-using-vary-header) در مقدار بستگی دارد. بنابراین تطبیق یک کلید جدید نیازمند نگاه کردن به هر دو کلید و مقدار برای ورودی‌های موجود در شیء `Cache` است.

> [!NOTE]
> API کش از headerهای کش HTTP پیروی نمی‌کند.

## متدهای نمونه

- {{domxref("Cache.match()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به پاسخ مرتبط با اولین درخواست مطابقت داده شده در شیء `Cache` حل می‌شود.
- {{domxref("Cache.matchAll()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به آرایه‌ای از تمام پاسخ‌های مطابقت داده شده در شیء `Cache` حل می‌شود.
- {{domxref("Cache.add()")}}
  - : یک URL را می‌گیرد، آن را بازیابی می‌کند و شیء پاسخ حاصل را به کش داده شده اضافه می‌کند. این از نظر عملکردی معادل فراخوانی `fetch()` و سپس استفاده از `put()` برای افزودن نتایج به کش است.
- {{domxref("Cache.addAll()")}}
  - : آرایه‌ای از URLها را می‌گیرد، آنها را بازیابی می‌کند و شیءهای پاسخ حاصل را به کش داده شده اضافه می‌کند.
- {{domxref("Cache.put()")}}
  - : هم یک درخواست و هم پاسخ آن را می‌گیرد و به کش داده شده اضافه می‌کند.
- {{domxref("Cache.delete()")}}
  - : ورودی `Cache` را که کلید آن درخواست است پیدا می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که اگر یک ورودی `Cache` مطابقت داده شده پیدا و حذف شود، به `true` حل می‌شود. اگر هیچ ورودی `Cache` یافت نشود، promise به `false` حل می‌شود.
- {{domxref("Cache.keys()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به آرایه‌ای از کلیدهای `Cache` حل می‌شود.

## مثال‌ها

این قطعه کد از [نمونه کش انتخابی service worker](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/selective-caching/service-worker.js) گرفته شده است. (به [کش انتخابی زنده](https://googlechrome.github.io/samples/service-worker/selective-caching/) مراجعه کنید.) کد از {{domxref("CacheStorage.open()")}} برای باز کردن هر شیء `Cache` با header `Content-Type` که با `font/` شروع می‌شود استفاده می‌کند.

سپس کد از {{domxref("Cache.match()")}} استفاده می‌کند تا ببیند آیا از قبل یک فونت مطابقت داده شده در کش وجود دارد یا خیر، و اگر وجود دارد، آن را برمی‌گرداند. اگر فونت مطابقت داده شده‌ای وجود نداشته باشد، کد فونت را از شبکه واکشی می‌کند و از {{domxref("Cache.put()")}} برای کش کردن منبع واکشی شده استفاده می‌کند.

کد استثناهای پرتاب شده از عملیات {{domxref("Window/fetch", "fetch()")}} را مدیریت می‌کند. توجه داشته باشید که یک پاسخ خطای HTTP (مثلاً 404) باعث ایجاد استثنا نخواهد شد. این یک شیء پاسخ عادی با کد خطای مناسب برمی‌گرداند.

قطعه کد همچنین یک بهترین روش برای نسخه‌بندی کش‌های استفاده شده توسط service worker را نشان می‌دهد. اگرچه در این مثال فقط یک کش وجود دارد، اما می‌توان از همین رویکرد برای چندین کش استفاده کرد. یک شناسه کوتاه برای یک کش به یک نام کش نسخه‌بندی شده خاص نگاشت می‌شود. کد همچنین تمام کش‌هایی که در `CURRENT_CACHES` نامگذاری نشده‌اند را حذف می‌کند.

در مثال کد، `caches` یک ویژگی از {{domxref("ServiceWorkerGlobalScope")}} است. این شامل شیء `CacheStorage` است که با آن می‌توان به رابط {{domxref("CacheStorage")}} دسترسی داشت.

> [!NOTE]
> در Chrome، برای مشاهده عبارات ورود به سیستم برای اقدامات مختلفی که اسکریپت [`service-worker.js`](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/selective-caching/service-worker.js) انجام می‌دهد، به `chrome://inspect/#service-workers` بروید و روی پیوند "inspect" زیر service worker ثبت‌شده کلیک کنید.

```js
const CACHE_VERSION = 1;
const CURRENT_CACHES = {
  font: `font-cache-v${CACHE_VERSION}`,
};

self.addEventListener("activate", (event) => {
  // Delete all caches that aren't named in CURRENT_CACHES.
  // While there is only one cache in this example, the same logic
  // will handle the case where there are multiple versioned caches.
  const expectedCacheNamesSet = new Set(Object.values(CURRENT_CACHES));
  event.waitUntil(
    caches.keys().then((cacheNames) =>
      Promise.all(
        cacheNames.map((cacheName) => {
          if (!expectedCacheNamesSet.has(cacheName)) {
            // If this cache name isn't present in the set of
            // "expected" cache names, then delete it.
            console.log("Deleting out of date cache:", cacheName);
            return caches.delete(cacheName);
          }
          return undefined;
        }),
      ),
    ),
  );
});

self.addEventListener("fetch", (event) => {
  console.log("Handling fetch event for", event.request.url);

  event.respondWith(
    caches
      .open(CURRENT_CACHES.font)
      .then((cache) => cache.match(event.request))
      .then((response) => {
        if (response) {
          // If there is an entry in the cache for event.request,
          // then response will be defined and we can just return it.
          // Note that in this example, only font resources are cached.
          console.log(" Found response in cache:", response);

          return response;
        }

        // Otherwise, if there is no entry in the cache for event.request,
        // response will be undefined, and we need to fetch() the resource.
        console.log(
          " No response for %s found in cache. About to fetch " +
            "from network…",
          event.request.url,
        );

        // We call .clone() on the request since we might use it
        // in a call to cache.put() later on.
        // Both fetch() and cache.put() "consume" the request,
        // so we need to make a copy.
        // (see https://developer.mozilla.org/en-US/docs/Web/API/Request/clone)
        return fetch(event.request.clone()).then((response) => {
          console.log(
            "  Response for %s from network is: %O",
            event.request.url,
            response,
          );

          if (
            response.status < 400 &&
            response.headers.has("content-type") &&
            response.headers.get("content-type").match(/^font\//i)
          ) {
            // This avoids caching responses that we know are errors
            // (i.e. HTTP status code of 4xx or 5xx).
            // We also only want to cache responses that correspond
            // to fonts, i.e. have a Content-Type response header that
            // starts with "font/".
            // Note that for opaque filtered responses
            // https://fetch.spec.whatwg.org/#concept-filtered-response-opaque
            // we can't access to the response headers, so this check will
            // always fail and the font won't be cached.
            // All of the Google Web Fonts are served from a domain that
            // supports CORS, so that isn't an issue here.
            // It is something to keep in mind if you're attempting
            // to cache other resources from a cross-origin
            // domain that doesn't support CORS, though!
            console.log("  Caching the response to", event.request.url);
            // We call .clone() on the response to save a copy of it
            // to the cache. By doing so, we get to keep the original
            // response object which we will return back to the controlled
            // page.
            // https://developer.mozilla.org/en-US/docs/Web/API/Request/clone
            cache.put(event.request, response.clone());
          } else {
            console.log("  Not caching the response to", event.request.url);
          }

          // Return the original response object, which will be used to
          // fulfill the resource request.
          return response;
        });
      })
      .catch((error) => {
        // This catch() will handle exceptions that arise from the match()
        // or fetch() operations.
        // Note that a HTTP error response (e.g. 404) will NOT trigger
        // an exception.
        // It will return a normal response object that has the appropriate
        // error code set.
        console.error("  Error in fetch handler:", error);

        throw error;
      }),
  );
});
```

### کوکی‌ها و اشیاء Cache

[API Fetch](/en-US/docs/Web/API/Fetch_API) نیاز دارد که headerهای {{httpheader("Set-Cookie")}} قبل از بازگرداندن یک شیء {{domxref("Response")}} از {{domxref("Window/fetch", "fetch()")}} حذف شوند. بنابراین یک `Response` ذخیره شده در یک `Cache` حاوی headerهای `Set-Cookie` نخواهد بود و در نتیجه باعث ذخیره هیچ کوکی‌ای نخواهد شد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workerها](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [مثال کد پایه Service workerها](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker)
- [استفاده از web workerها](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)