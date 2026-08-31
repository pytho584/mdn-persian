---
title: "CacheStorage: match() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/match"
translated_by: "n8n + AI"
---

---
title: "CacheStorage: match() method"
short-title: match()
slug: Web/API/CacheStorage/match
page-type: web-api-instance-method
browser-compat: api.CacheStorage.match
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`match()`** از رابط {{domxref("CacheStorage")}} بررسی می‌کند که آیا یک {{domxref("Request")}} داده‌شده یا رشته‌ی URL معین، کلیدی برای یک {{domxref("Response")}} ذخیره‌شده است.
این متد یک {{jsxref("Promise")}} برای یک {{domxref("Response")}} برمی‌گرداند، یا یک {{jsxref("Promise")}} که در صورت یافت نشدن هیچ تطابقی به `undefined` حل می‌شود.

می‌توانید از طریق ویژگی {{domxref("Window.caches")}} در پنجره‌ها یا ویژگی {{domxref("WorkerGlobalScope.caches")}} در کارگران به `CacheStorage` دسترسی پیدا کنید.

اشیاء `Cache` به ترتیب ایجاد جستجو می‌شوند.

> [!NOTE]
> `caches.match()` یک متد راحت است.
> عملکرد معادل آن است که {{domxref("cache.match()")}} را روی هر کش (به ترتیب بازگردانده‌شده توسط {{domxref("CacheStorage.keys()", "caches.keys()")}}) صدا بزنید تا زمانی که یک {{domxref("Response")}} برگردانده شود.

## نحو

```js-nolint
match(request)
match(request, options)
```

### پارامترها

- `request`
  - : {{domxref("Request")}} که می‌خواهید مطابقت دهید. این می‌تواند یک شیء {{domxref("Request")}} یا یک رشته‌ی URL باشد.
- `options` {{optional_inline}}
  - : یک شیء که ویژگی‌های آن نحوه انجام مطابقت در عملیات `match` را کنترل می‌کنند. گزینه‌های موجود عبارتند از:
    - `ignoreSearch`
      - : یک مقدار بولی که مشخص می‌کند آیا فرآیند مطابقت باید رشته‌ی جستجو (query string) در URL را نادیده بگیرد. به عنوان مثال، اگر روی `true` تنظیم شود، بخش `?value=bar` از `https://example.com/?value=bar` هنگام انجام مطابقت نادیده گرفته می‌شود. پیش‌فرض `false` است.
    - `ignoreMethod`
      - : یک مقدار بولی که وقتی روی `true` تنظیم شود، از اعتبارسنجی متد `http` در {{domxref("Request")}} جلوگیری می‌کند (به طور معمول فقط `GET` و `HEAD` مجاز هستند). پیش‌فرض `false` است.
    - `ignoreVary`
      - : یک مقدار بولی که وقتی روی `true` تنظیم شود، به عملیات مطابقت می‌گوید که مطابقت هدر `VARY` را انجام ندهد. به عبارت دیگر، اگر URL مطابقت داشت، بدون توجه به اینکه شیء {{domxref("Response")}} هدر `VARY` دارد یا نه، تطابق خواهید گرفت. پیش‌فرض `false` است.
    - `cacheName`
      - : یک رشته که یک کش خاص را برای جستجو در داخل آن نشان می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{domxref("Response")}} مطابق حل می‌شود. اگر پاسخی مطابق با درخواست مشخص‌شده یافت نشود، پرامیس با `undefined` حل می‌شود.

## مثال‌ها

این مثال از [مثال سرویس‌ورکر ساده MDN](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker) گرفته شده است (همچنین [اجرای زنده سرویس‌ورکر ساده](https://bncb2v.csb.app/)).
در اینجا منتظر شروع یک {{domxref("FetchEvent")}} می‌مانیم. یک پاسخ سفارشی به این صورت می‌سازیم:

1. بررسی می‌کنیم که آیا تطابقی برای درخواست در {{domxref("CacheStorage")}} با استفاده از `CacheStorage.match()` پیدا می‌شود. اگر بله، آن را سرو می‌کنیم.
2. اگر نه، کش `v1` را با استفاده از `open()` باز می‌کنیم، درخواست شبکه پیش‌فرض را با استفاده از {{domxref("Cache.put","Cache.put()")}} در کش قرار می‌دهیم و یک کلون از درخواست شبکه پیش‌فرض را با استفاده از `return response.clone()` برمی‌گردانیم. مورد آخر ضروری است زیرا `put()` بدنه پاسخ را مصرف می‌کند.
3. اگر این کار ناموفق بود (مثلاً به دلیل قطع بودن شبکه)، یک پاسخ جایگزین برمی‌گردانیم.

```js
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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}