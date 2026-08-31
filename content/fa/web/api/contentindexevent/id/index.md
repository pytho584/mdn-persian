---
title: "ContentIndexEvent: id property"
short-title: id
slug: Web/API/ContentIndexEvent/id
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ContentIndexEvent.id
---

{{APIRef("Content Index API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

خاصیت فقط-خواندنی **`id`** از رابط {{domxref("ContentIndexEvent")}} یک {{jsxref('String')}} است که شاخص محتوای حذف‌شده را از طریق `id` آن شناسایی می‌کند.

## مقدار

یک {{jsxref("String")}} که نمایانگر شناسه شاخص محتوای حذف‌شده است.

## مثال‌ها

این مثال به رویداد {{domxref('ContentIndexEvent', 'contentdelete')}} گوش می‌دهد و شناسه شاخص محتوای حذف‌شده را ثبت می‌کند.

{{domxref('ContentIndexEvent')}} فقط در [حوزه سراسری](/en-US/docs/Web/API/ServiceWorkerGlobalScope) یک {{domxref('ServiceWorker')}} در دسترس است.

```js
self.addEventListener("contentdelete", (event) => {
  console.log(event.id);

  // logs content index id, which can then be used to determine what content to delete from your cache
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [یک مقاله مقدماتی درباره Content Index API](https://developer.chrome.com/docs/capabilities/web-apis/content-indexing-api)
- [Service Worker API، به همراه اطلاعاتی درباره Cache و CacheStorage](/en-US/docs/Web/API/Service_Worker_API)