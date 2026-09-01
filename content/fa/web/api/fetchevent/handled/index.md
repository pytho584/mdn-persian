---
title: "FetchEvent: handled property"
short-title: handled
slug: Web/API/FetchEvent/handled
page-type: web-api-instance-property
browser-compat: api.FetchEvent.handled
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

خاصیت **`handled`** از رابط {{DOMxRef("FetchEvent")}} یک {{jsxref("Promise")}} برمی‌گرداند که نشان می‌دهد آیا رویداد توسط الگوریتم fetch پردازش شده است یا خیر. این خاصیت امکان اجرای کد پس از مصرف پاسخ توسط مرورگر را فراهم می‌کند و معمولاً به همراه متد {{DOMxRef("ExtendableEvent.waitUntil", "waitUntil()")}} استفاده می‌شود.

## مقدار

یک {{jsxref("Promise")}} که تا زمانی که رویداد پردازش نشده است در حالت انتظار (pending) قرار دارد و پس از پردازش تکمیل (fulfilled) می‌شود.

## مثال

```js
addEventListener("fetch", (event) => {
  event.respondWith(
    (async function () {
      const response = await doCalculateAResponse(event.request);

      event.waitUntil(
        (async function () {
          await doSomeAsyncStuff(); // optional

          // Wait for the event to be consumed by the browser
          await event.handled;

          return doFinalStuff(); // Finalize AFTER the event has been consumed
        })(),
      );

      return response;
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("ExtendableEvent.waitUntil()")}}