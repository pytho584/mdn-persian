---
title: "CacheStorage"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage"
translated_by: "n8n + AI"
---

---
title: CacheStorage
slug: Web/API/CacheStorage
page-type: web-api-interface
browser-compat: api.CacheStorage
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

رابط **`CacheStorage`** نمایانگر ذخیره‌سازی برای اشیاء {{domxref("Cache")}} است.

این رابط:

- یک دایرکتوری اصلی از تمام کش‌های نام‌گذاری شده که توسط یک {{domxref("ServiceWorker")}} یا نوع دیگری از کارگر یا محدوده {{domxref("window")}} قابل دسترسی است، فراهم می‌کند (شما محدود به استفاده فقط با سرویس‌ورکرها نیستید).
- یک نگاشت از نام‌های رشته‌ای به اشیاء {{domxref("Cache")}} مربوطه را حفظ می‌کند.

از {{domxref("CacheStorage.open()")}} برای دریافت یک نمونه {{domxref("Cache")}} استفاده کنید.

از {{domxref("CacheStorage.match()")}} برای بررسی اینکه آیا یک {{domxref("Request")}} داده شده یک کلید در هر یک از اشیاء {{domxref("Cache")}} است که شیء `CacheStorage` آن‌ها را ردیابی می‌کند، استفاده کنید.

شما می‌توانید به `CacheStorage` از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا از طریق ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگرها دسترسی داشته باشید.

> [!NOTE]
> `CacheStorage` همیشه در مبدأهای نامعتبر (یعنی آن‌هایی که از HTTPS استفاده نمی‌کنند، اگرچه این تعریف احتمالاً در آینده پیچیده‌تر خواهد شد) با یک `SecurityError` رد می‌شود. هنگام آزمایش در Firefox، می‌توانید با علامت زدن گزینه **Enable Service Workers over HTTP (when toolbox is open)** در منوی گزینه‌ها/چرخ دنده Firefox DevTools از این مشکل عبور کنید. علاوه بر این، از آنجایی که `CacheStorage` به دسترسی به سیستم فایل نیاز دارد، ممکن است در حالت خصوصی Firefox در دسترس نباشد.

> [!NOTE]
> {{domxref("CacheStorage.match()")}} یک روش راحت است. عملکرد مشابه برای تطبیق یک ورودی کش می‌تواند با بازگرداندن آرایه‌ای از نام‌های کش از {{domxref("CacheStorage.keys()")}}، باز کردن هر کش با {{domxref("CacheStorage.open()")}} و تطبیق مورد نظر با {{domxref("Cache.match()")}} پیاده‌سازی شود.

## روش‌های نمونه

- {{domxref("CacheStorage.match()")}}
  - : بررسی می‌کند که آیا یک {{domxref("Request")}} داده شده یک کلید در هر یک از اشیاء {{domxref("Cache")}} است که شیء `CacheStorage` آن‌ها را ردیابی می‌کند، و یک {{jsxref("Promise")}} برمی‌گرداند که به آن تطبیق حل می‌شود.
- {{domxref("CacheStorage.has()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که اگر یک شیء {{domxref("Cache")}} مطابق با `cacheName` وجود داشته باشد، به `true` حل می‌شود.
- {{domxref("CacheStorage.open()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به شیء {{domxref("Cache")}} مطابق با `cacheName` حل می‌شود (اگر از قبل وجود نداشته باشد، یک کش جدید ایجاد می‌شود.)
- {{domxref("CacheStorage.delete()")}}
  - : شیء {{domxref("Cache")}} مطابق با `cacheName` را پیدا می‌کند، و اگر پیدا شود، شیء {{domxref("Cache")}} را حذف می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که به `true` حل می‌شود. اگر هیچ شیء {{domxref("Cache")}} پیدا نشود، به `false` حل می‌شود.
- {{domxref("CacheStorage.keys()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با آرایه‌ای حاوی رشته‌های مربوط به تمام اشیاء {{domxref("Cache")}} نام‌گذاری شده که توسط `CacheStorage` ردیابی می‌شوند، حل می‌شود. از این روش برای پیمایش لیست تمام اشیاء {{domxref("Cache")}} استفاده کنید.

## مثال‌ها

این قطعه کد از [مثال سرویس‌ورکر ساده MDN](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker) است ( [مثال سرویس‌ورکر ساده در حال اجرا](https://bncb2v.csb.app/) را ببینید.)
این اسکریپت سرویس‌ورکر منتظر می‌ماند تا یک رویداد {{domxref("ServiceWorkerGlobalScope/install_event", "install")}} فعال شود، سپس {{domxref("ExtendableEvent.waitUntil","waitUntil")}} را برای مدیریت فرآیند نصب برنامه اجرا می‌کند. این شامل فراخوانی {{domxref("CacheStorage.open")}} برای ایجاد یک کش جدید، سپس استفاده از {{domxref("Cache.addAll")}} برای افزودن مجموعه‌ای از دارایی‌ها به آن است.

در بلوک کد دوم، منتظر می‌مانیم تا یک {{domxref("FetchEvent")}} فعال شود. یک پاسخ سفارشی به صورت زیر می‌سازیم:

1. بررسی کنید که آیا تطبیقی برای درخواست در CacheStorage پیدا شده است. اگر چنین است، آن را ارائه دهید.
2. اگر نه، درخواست را از شبکه دریافت کنید، سپس کش ایجاد شده در بلوک اول را باز کنید و یک کلون از درخواست را با استفاده از {{domxref("Cache.put")}} (`cache.put(event.request, response.clone())`) به آن اضافه کنید.
3. اگر این کار ناموفق بود (مثلاً به دلیل قطع شدن شبکه)، یک پاسخ بازگشتی برگردانید.

در نهایت، هر چیزی که پاسخ سفارشی برابر با آن شد را با استفاده از {{domxref("FetchEvent.respondWith")}} برگردانید.

```js
self.addEventListener("install", (event) => {
  event.waitUntil(
    caches
      .open("v1")
      .then((cache) =>
        cache.addAll([
          "/",
          "/index.html",
          "/style.css",
          "/app.js",
          "/image-list.js",
          "/star-wars-logo.jpg",
          "/gallery/bountyHunters.jpg",
          "/gallery/myLittleVader.jpg",
          "/gallery/snowTroopers.jpg",
        ]),
      ),
  );
});

self.addEventListener("fetch", (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      // caches.match() always resolves
      // but in case of success response will have value
      if (response !== undefined) {
        return response;
      }
      return fetch(event.request)
        .then((response) => {
          // response may be used only once
          // we need to save clone to put one copy in cache
          // and serve second one
          let responseClone = response.clone();

          caches
            .open("v1")
            .then((cache) => cache.put(event.request, responseClone));
          return response;
        })
        .catch(() => caches.match("/gallery/myLittleVader.jpg"));
    }),
  );
});
```

این قطعه نشان می‌دهد که چگونه می‌توان از API خارج از زمینه سرویس‌ورکر استفاده کرد، و از عملگر `await` برای کد بسیار خواناتر استفاده می‌کند.

```js
// Try to get data from the cache, but fall back to fetching it live.
async function getData() {
  const cacheVersion = 1;
  const cacheName = `myapp-${cacheVersion}`;
  const url = "https://jsonplaceholder.typicode.com/todos/1";
  let cachedData = await getCachedData(cacheName, url);

  if (cachedData) {
    console.log("Retrieved cached data");
    return cachedData;
  }

  console.log("Fetching fresh data");

  const cacheStorage = await caches.open(cacheName);
  await cacheStorage.add(url);
  cachedData = await getCachedData(cacheName, url);
  await deleteOldCaches(cacheName);

  return cachedData;
}

// Get data from the cache.
async function getCachedData(cacheName, url) {
  const cacheStorage = await caches.open(cacheName);
  const cachedResponse = await cacheStorage.match(url);

  if (!cachedResponse || !cachedResponse.ok) {
    return false;
  }

  return await cachedResponse.json();
}

// Delete any old caches to respect user's disk space.
async function deleteOldCaches(currentCache) {
  const keys = await caches.keys();

  for (const key of keys) {
    const isOurCache = key.startsWith("myapp-");
    if (currentCache === key || !isOurCache) {
      continue;
    }
    caches.delete(key);
  }
}

try {
  const data = await getData();
  console.log({ data });
} catch (error) {
  console.error({ error });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از سرویس‌ورکرها](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}
- [حالت‌های مرور خصوصی / ناشناس](/en-US/docs/Web/API/Web_Storage_API#private_browsing_incognito_modes)