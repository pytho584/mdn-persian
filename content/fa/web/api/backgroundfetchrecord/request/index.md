---
title: "BackgroundFetchRecord: request property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRecord/request"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRecord: request property"
short-title: request
slug: Web/API/BackgroundFetchRecord/request
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRecord.request
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`request`** در رابط {{domxref("BackgroundFetchRecord")}} جزئیات منبع مورد نظر برای دریافت را برمی‌گرداند.

## Value

یک {{domxref("Request")}}.

## Examples

در این مثال، یک `BackgroundFetchRecord` با استفاده از {{domxref("BackgroundFetchManager.fetch()","BackgroundFetchManager.fetch()")}} برگردانده می‌شود. سپس `request` بازگردانده و در کنسول ثبت می‌شود.

```js
bgFetch.match("/ep-5.mp3").then(async (record) => {
  if (!record) {
    console.log("No record found");
    return;
  }

  console.log(`Here's the request`, record.request);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}