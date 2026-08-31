---
title: "BackgroundFetchRecord"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRecord"
translated_by: "n8n + AI"
---

---
title: BackgroundFetchRecord
slug: Web/API/BackgroundFetchRecord
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BackgroundFetchRecord
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رابط **`BackgroundFetchRecord`** از {{domxref('Background Fetch API','','',' ')}} نشان‌دهنده‌ی یک درخواست و پاسخ مجزا است.

یک `BackgroundFetchRecord` توسط متد {{domxref("BackgroundFetchRegistration.match()","BackgroundFetchRegistration.matchAll()")}} ایجاد می‌شود، بنابراین هیچ سازنده‌ای برای این رابط وجود ندارد.

برای هر منبعی که توسط `fetch()` درخواست می‌شود، یک `BackgroundFetchRecord` وجود خواهد داشت.

## ویژگی‌های نمونه

- {{domxref("BackgroundFetchRecord.request","request")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("Request")}} را برمی‌گرداند.
- {{domxref("BackgroundFetchRecord.responseReady","responseReady")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک promise را برمی‌گرداند که با یک {{domxref("Response")}} حل می‌شود.

## مثال‌ها

در این مثال، یک `BackgroundFetchRecord` مجزا با استفاده از {{domxref("BackgroundFetchRegistration.match()","BackgroundFetchRegistration.matchAll()")}} برگردانده می‌شود. {{domxref("BackgroundFetchRecord.request")}} و {{domxref("BackgroundFetchRecord.responseReady")}} برگردانده شده و در کنسول ثبت می‌شوند.

```js
bgFetch.match("/ep-5.mp3").then(async (record) => {
  if (!record) {
    console.log("No record found");
    return;
  }

  console.log(`Here's the request`, record.request);
  const response = await record.responseReady;
  console.log(`And here's the response`, response);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}