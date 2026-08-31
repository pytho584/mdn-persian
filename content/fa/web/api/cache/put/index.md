---
title: "Cache: put() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/put"
translated_by: "n8n + AI"
---

---
title: "Cache: put() method"
short-title: put()
slug: Web/API/Cache/put
page-type: web-api-instance-method
browser-compat: api.Cache.put
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`put()`** از رابط {{domxref("Cache")}} اجازه می‌دهد جفت‌های کلید/مقدار به شیء فعلی {{domxref("Cache")}} اضافه شوند.

اغلب، شما فقط می‌خواهید یک یا چند درخواست را با {{domxref("Window/fetch", "fetch()")}} واکشی کنید و سپس نتیجه را مستقیماً به کش خود اضافه کنید. در چنین مواردی بهتر است از {{domxref("Cache.add","Cache.add()")}}/{{domxref("Cache.addAll","Cache.addAll()")}} استفاده کنید، زیرا آن‌ها توابع خلاصه‌نویسی برای یک یا چند مورد از این عملیات هستند.

```js
fetch(url).then((response) => {
  if (!response.ok) {
    throw new TypeError("Bad response status");
  }
  return cache.put(url, response);
});
```

> [!NOTE]
> `put()` هر جفت کلید/مقداری را که قبلاً در کش ذخیره شده و با درخواست مطابقت دارد، بازنویسی خواهد کرد.

> [!NOTE]
> {{domxref("Cache.add")}}/{{domxref("Cache.addAll")}} پاسخ‌هایی را که `Response.status` آن‌ها در محدوده 200 نیست، کش نمی‌کنند، در حالی که `Cache.put` به شما اجازه می‌دهد هر جفت درخواست/پاسخی را ذخیره کنید. در نتیجه، {{domxref("Cache.add")}}/{{domxref("Cache.addAll")}} نمی‌توانند برای ذخیره پاسخ‌های غیرشفاف استفاده شوند، اما `Cache.put` می‌تواند.

## سینتکس

```js-nolint
put(request, response)
```

### پارامترها

- `request`
  - : شیء {{domxref("Request")}} یا آدرس URL که می‌خواهید به کش اضافه کنید.
- `response`
  - : شیء {{domxref("Response")}} که می‌خواهید با درخواست مطابقت دهید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با `undefined` حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر طرح URL (scheme) به غیر از `http` یا `https` باشد، برگردانده می‌شود.

## نمونه‌ها

این مثال از [نمونه simple-service-worker](https://github.com/mdn/dom-examples/tree/main/service-worker/simple-service-worker) متعلق به MDN است (همچنین ببینید [simple-service-worker اجرای زنده](https://bncb2v.csb.app/)).
در اینجا منتظر رخ دادن یک {{domxref("FetchEvent")}} می‌مانیم. یک پاسخ سفارشی به صورت زیر می‌سازیم:

1. بررسی می‌کنیم که آیا مطابقتی برای درخواست در {{domxref("CacheStorage")}} با استفاده از {{domxref("CacheStorage.match","CacheStorage.match()")}} یافت می‌شود یا نه. اگر یافت شد، آن را سرو می‌کنیم.
2. اگر یافت نشد، کش `v1` را با استفاده از `open()` باز می‌کنیم، درخواست شبکه پیش‌فرض را با استفاده از `Cache.put()` در کش قرار می‌دهیم و یک کپی از درخواست شبکه پیش‌فرض را با `return response.clone()` بازمی‌گردانیم. کپی موردنیاز است زیرا `put()` بدنه پاسخ را مصرف می‌کند.
3. اگر این کار ناموفق بود (مثلاً به دلیل قطع بودن شبکه)، یک پاسخ جایگزین بازمی‌گردانیم.

```js
let response;
const cachedResponse = caches
  .match(event.request)
  .then((r) => (r !== undefined ? r : fetch(event.request)))
  .then((r) => {
    response = r;
    caches.open("v1").then((cache) => cache.put(event.request, response));
    return response.clone();
  })
  .catch(() => caches.match("/gallery/myLittleVader.jpg"));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}