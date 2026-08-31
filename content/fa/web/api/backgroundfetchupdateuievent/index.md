---
title: "BackgroundFetchUpdateUIEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchUpdateUIEvent"
translated_by: "n8n + AI"
---

---
title: BackgroundFetchUpdateUIEvent
slug: Web/API/BackgroundFetchUpdateUIEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BackgroundFetchUpdateUIEvent
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

رابطهٔ **`BackgroundFetchUpdateUIEvent`** از {{domxref('Background Fetch API','','',' ')}} نوعی رویداد برای رویدادهای {{domxref("ServiceWorkerGlobalScope.backgroundfetchsuccess_event", "backgroundfetchsuccess")}} و {{domxref("ServiceWorkerGlobalScope.backgroundfetchfail_event", "backgroundfetchfail")}} است و روشی برای به‌روزرسانی عنوان و نماد برنامه فراهم می‌کند تا کاربر از موفقیت یا شکست یک دریافت پس‌زمینه مطلع شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("BackgroundFetchUpdateUIEvent.BackgroundFetchUpdateUIEvent()", "BackgroundFetchUpdateUIEvent()")}} {{Experimental_Inline}}
  - : یک شیء `BackgroundFetchUIEvent` جدید ایجاد می‌کند. این سازنده معمولاً استفاده نمی‌شود، زیرا مرورگر خودش این اشیاء را برای رویدادهای {{domxref("ServiceWorkerGlobalScope.backgroundfetchsuccess_event", "backgroundfetchsuccess")}} و {{domxref("ServiceWorkerGlobalScope.backgroundfetchfail_event", "backgroundfetchfail")}} می‌سازد.

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("BackgroundFetchEvent")}} را به ارث می‌برد._

## متدهای نمونه

_همچنین متدهای والد خود، {{domxref("BackgroundFetchEvent")}} را به ارث می‌برد._

- {{domxref("BackgroundFetchUpdateUIEvent.updateUI()")}} {{Experimental_Inline}}
  - : عنوان و نماد را در رابط کاربری به‌روزرسانی می‌کند تا وضعیت یک دریافت پس‌زمینه را نشان دهد. با یک {{jsxref("Promise")}} حل می‌شود.

## مثال‌ها

در این مثال، رویداد `backgroundfetchsuccess` شنیده می‌شود که نشان می‌دهد یک دریافت با موفقیت کامل شده است. سپس متد {{domxref("BackgroundFetchUpdateUIEvent.updateUI()", "updateUI()")}} با یک پیام فراخوانی می‌شود تا به کاربر اطلاع دهد قسمتی که دانلود کرده آماده است.

```js
addEventListener("backgroundfetchsuccess", (event) => {
  const bgFetch = event.registration;

  event.waitUntil(
    (async () => {
      // Create/open a cache.
      const cache = await caches.open("downloads");
      // Get all the records.
      const records = await bgFetch.matchAll();
      // Copy each request/response across.
      const promises = records.map(async (record) => {
        const response = await record.responseReady;
        await cache.put(record.request, response);
      });

      // Wait for the copying to complete.
      await Promise.all(promises);

      // Update the progress notification.
      event.updateUI({ title: "Episode 5 ready to listen!" });
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}