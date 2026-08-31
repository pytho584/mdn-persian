---
title: "Cache: match() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/match"
translated_by: "n8n + AI"
---

---
title: "Cache: match() method"
short-title: match()
slug: Web/API/Cache/match
page-type: web-api-instance-method
browser-compat: api.Cache.match
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`match()`** از رابط {{domxref("Cache")}} یک {{jsxref("Promise")}} برمی‌گرداند که به {{domxref("Response")}} مرتبط با اولین درخواست منطبق در شیء {{domxref("Cache")}} تحقق می‌یابد.
اگر هیچ تطابقی یافت نشود، {{jsxref("Promise")}} به {{jsxref("undefined")}} تحقق می‌یابد.

## نحو (Syntax)

```js-nolint
match(request)
match(request, options)
```

### پارامترها

- `request`
  - : {{domxref("Request")}} که برای آن تلاش می‌کنید پاسخ‌ها را در {{domxref("Cache")}} بیابید. این می‌تواند یک شیء {{domxref("Request")}} یا یک رشته URL باشد.
- `options` {{optional_inline}}
  - : شیءای که گزینه‌هایی را برای عملیات `match` تنظیم می‌کند.
    گزینه‌های موجود عبارتند از:
    - `ignoreSearch`
      - : یک مقدار بولین که مشخص می‌کند آیا رشته جستجو (query string) در URL نادیده گرفته شود یا نه. برای مثال، اگر روی `true` تنظیم شود، بخش `?value=bar` از `https://example.com/?value=bar` هنگام انجام تطبیق نادیده گرفته می‌شود. پیش‌فرض آن `false` است.
    - `ignoreMethod`
      - : یک مقدار بولین که وقتی روی `true` تنظیم شود، از اعتبارسنجی متد `http` در {{domxref("Request")}} توسط عملیات تطبیق جلوگیری می‌کند (معمولاً فقط `GET` و `HEAD` مجاز هستند). پیش‌فرض آن `false` است.
    - `ignoreVary`
      - : یک مقدار بولین که وقتی روی `true` تنظیم شود، به عملیات تطبیق می‌گوید که تطبیق هدر `VARY` را انجام ندهد — یعنی اگر URL مطابقت داشته باشد، بدون توجه به اینکه شیء {{domxref("Response")}} هدر `VARY` دارد یا نه، تطبیق انجام می‌شود. پیش‌فرض آن `false` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به اولین {{domxref("Response")}} منطبق با درخواست، یا در صورت عدم یافتن تطبیق، به {{jsxref("undefined")}} تحقق می‌یابد.

> [!NOTE]
> `Cache.match()` اساساً با {{domxref("Cache.matchAll()")}} یکسان است، با این تفاوت که به جای تحقق با آرایه‌ای از همه پاسخ‌های منطبق، فقط با اولین پاسخ منطبق تحقق می‌یابد (یعنی `response[0]`).

## مثال‌ها

این مثال از نمونه [صفحه آفلاین سفارشی](https://github.com/GoogleChrome/samples/blob/gh-pages/service-worker/custom-offline-page/service-worker.js) گرفته شده است ([دموی زنده](https://googlechrome.github.io/samples/service-worker/custom-offline-page/index.html)). این مثال از یک کش برای تأمین داده‌های انتخاب‌شده وقتی درخواست شکست می‌خورد استفاده می‌کند. یک بند `catch()` زمانی فعال می‌شود که فراخوانی `fetch()` یک استثنا پرتاب کند. در داخل بند `catch()`، از `match()` برای بازگرداندن پاسخ صحیح استفاده می‌شود.

در این مثال، فقط اسناد HTML که با فعل HTTP GET دریافت می‌شوند کش می‌شوند. اگر شرط `if ()` ما نادرست باشد، این هندلر fetch درخواست را رهگیری نمی‌کند. اگر هر هندلر fetch دیگری ثبت شده باشد، آن‌ها فرصت خواهند داشت تا `event.respondWith()` را فراخوانی کنند. اگر هیچ هندلر fetch ای `event.respondWith()` را فراخوانی نکند، درخواست توسط مرورگر طوری مدیریت می‌شود که گویی هیچ سرویس‌ورکاری درگیر نیست. اگر `fetch()` یک پاسخ HTTP معتبر با کد پاسخ در محدوده 4xx یا 5xx برگرداند، `catch()` فراخوانی **نخواهد** شد.

```js
self.addEventListener("fetch", (event) => {
  // We only want to call event.respondWith() if this is a GET request for an HTML document.
  if (
    event.request.method === "GET" &&
    event.request.headers.get("accept").includes("text/html")
  ) {
    console.log("Handling fetch event for", event.request.url);
    event.respondWith(
      fetch(event.request).catch((e) => {
        console.error("Fetch failed; returning offline page instead.", e);
        return caches
          .open(OFFLINE_CACHE)
          .then((cache) => cache.match(OFFLINE_URL));
      }),
    );
  }
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