---
title: "BackgroundFetchEvent: registration property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchEvent/registration"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchEvent: registration property"
short-title: registration
slug: Web/API/BackgroundFetchEvent/registration
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchEvent.registration
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`registration`** از رابط {{domxref("BackgroundFetchEvent")}} یک شیء {{domxref("BackgroundFetchRegistration")}} را برمی‌گرداند.

## مقدار

یک {{domxref("BackgroundFetchRegistration")}}.

## مثال‌ها

در این مثال، اگر کاربر بر روی رابط کاربری نمایش‌دهنده پیشرفت دانلود کلیک کند، رویداد {{domxref("ServiceWorkerGlobalScope/backgroundfetchclick_event", "backgroundfetchclick")}} فعال می‌شود. {{domxref("BackgroundFetchRegistration")}} فعلی با فراخوانی `event.registration` برگردانده می‌شود.

```js
addEventListener("backgroundfetchclick", (event) => {
  console.log(event.registration);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}