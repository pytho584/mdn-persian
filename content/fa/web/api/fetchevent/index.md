---
title: "FetchEvent"
---

---
title: FetchEvent
slug: Web/API/FetchEvent
page-type: web-api-interface
browser-compat: api.FetchEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

این نوع رویداد برای رویدادهای `fetch` است که در {{domxref("ServiceWorkerGlobalScope", "حوزهٔ سراسری سرویس‌ورکر", "", 1)}} ارسال می‌شوند. این رویداد شامل اطلاعاتی دربارهٔ درخواست (fetch) است، از جمله خود درخواست و نحوهٔ برخورد گیرنده با پاسخ. همچنین متد {{domxref("FetchEvent.respondWith", "event.respondWith()")}} را فراهم می‌کند که به ما امکان می‌دهد پاسخی برای این درخواست ارائه دهیم.

{{InheritanceDiagram}}

## سازنده

- {{domxref("FetchEvent.FetchEvent()", "FetchEvent()")}}
  - : یک شیء جدید `FetchEvent` ایجاد می‌کند. معمولاً از این سازنده استفاده نمی‌شود؛ مرورگر این اشیاء را می‌سازد و آن‌ها را به فراخوانی‌های رویداد `fetch` ارائه می‌دهد.

## ویژگی‌های نمونه

_ویژگی‌ها را از ancestor خود، {{domxref("Event")}} به ارث می‌برد._

- {{domxref("FetchEvent.clientId")}} {{ReadOnlyInline}}
  - : {{domxref("Client.id", "شناسه")}} {{domxref("Client", "کلاینتی")}} که درخواست را آغاز کرده و هم‌ریشه (same-origin) است.
- {{domxref("FetchEvent.handled")}} {{ReadOnlyInline}}
  - : یک وعده (promise) که تا زمانی که رویداد مدیریت نشده در حالت معلق است و پس از مدیریت، fulfilled می‌شود.
- {{domxref("FetchEvent.isReload")}} {{ReadOnlyInline}} {{Deprecated_inline}} {{Non-standard_inline}}
  - : اگر رویداد توسط کاربری که سعی در بارگذاری مجدد صفحه دارد ارسال شده باشد، `true` و در غیر این صورت `false` برمی‌گرداند.
- {{domxref("FetchEvent.preloadResponse")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برای یک {{domxref("Response")}}، یا اگر این درخواست یک ناوبری نباشد یا [بارگذاری پیش‌گیرانهٔ ناوبری](/en-US/docs/Web/API/NavigationPreloadManager) فعال نبوده باشد، `undefined` برمی‌گرداند.
- {{domxref("FetchEvent.replacesClientId")}} {{ReadOnlyInline}}
  - : {{domxref("Client.id", "شناسه")}} {{domxref("Client", "کلاینتی")}} که در طول ناوبری صفحه جایگزین می‌شود.
- {{domxref("FetchEvent.resultingClientId")}} {{ReadOnlyInline}}
  - : {{domxref("Client.id", "شناسه")}} {{domxref("Client", "کلاینتی")}} که در طول ناوبری صفحه، کلاینت قبلی را جایگزین می‌کند.
- {{domxref("FetchEvent.request")}} {{ReadOnlyInline}}
  - : {{domxref("Request")}} که مرورگر قصد ارسال آن را دارد.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("ExtendableEvent")}} به ارث می‌برد._

- {{domxref("FetchEvent.respondWith()")}}
  - : از مدیریت پیش‌فرض fetch توسط مرورگر جلوگیری کرده و خودتان (وعده‌ای برای) یک پاسخ ارائه می‌دهید.
- {{domxref("ExtendableEvent.waitUntil()")}}
  - : طول عمر رویداد را افزایش می‌دهد. برای اطلاع‌رسانی به مرورگر دربارهٔ کارهایی که فراتر از بازگرداندن یک پاسخ هستند (مانند استریم و کش‌کردن) استفاده می‌شود.

## مثال‌ها

این رویداد fetch برای درخواست‌های غیر از GET از رفتار پیش‌فرض مرورگر استفاده می‌کند.
برای درخواست‌های GET، تلاش می‌کند یک مورد منطبق در کش پیدا کند و در نبود آن به شبکه مراجعه می‌کند. اگر مورد منطبق در کش یافت شود، به‌صورت ناهمگام کش را برای دفعهٔ بعد به‌روزرسانی می‌کند.

```js
self.addEventListener("fetch", (event) => {
  // بگذارید مرورگر کار پیش‌فرض خود را
  // برای درخواست‌های غیر از GET انجام دهد.
  if (event.request.method !== "GET") return;

  // جلوگیری از رفتار پیش‌فرض، و مدیریت خودمان درخواست.
  event.respondWith(
    (async () => {
      // تلاش برای دریافت پاسخ از کش.
      const cache = await caches.open("dynamic-v1");
      const cachedResponse = await cache.match(event.request);

      if (cachedResponse) {
        // اگر مورد منطبق در کش یافت شد، آن را برگردان، اما
        // ورودی مربوطه در کش را نیز در پس‌زمینه به‌روزرسانی کن.
        event.waitUntil(cache.add(event.request));
        return cachedResponse;
      }

      // اگر مورد منطبق در کش یافت نشد، از شبکه استفاده کن.
      return fetch(event.request);
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویداد `fetch`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/fetch_event)
- {{jsxref("Promise")}}
- [Fetch API](/en-US/docs/Web/API/Fetch_API)