---
title: "BackgroundFetchRecord: responseReady property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRecord/responseReady"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRecord: responseReady property"
short-title: responseReady
slug: Web/API/BackgroundFetchRecord/responseReady
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRecord.responseReady
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقطخواندنی **`responseReady`** در رابط {{domxref("BackgroundFetchRecord")}} یک {{jsxref("Promise")}} را برمی‌گرداند که با یک {{domxref("Response")}} حل می‌شود.

## مقدار

یک {{jsxref("Promise")}} که با یک {{domxref("Response")}} حل می‌شود.

## مثال‌ها

در این مثال، یک `BackgroundFetchRecord` به‌صورت تکی با استفاده از {{domxref("BackgroundFetchManager.fetch()","BackgroundFetchManager.fetch()")}} برگردانده می‌شود. مقدار `responseReady` برگردانده شده و در کنسول ثبت می‌شود.

```js
bgFetch.match("/ep-5.mp3").then(async (record) => {
  if (!record) {
    console.log("No record found");
    return;
  }

  const response = await record.responseReady;
  console.log(`Here's the response`, response);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}