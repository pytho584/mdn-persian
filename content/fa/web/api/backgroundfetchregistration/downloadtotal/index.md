---
title: "BackgroundFetchRegistration: downloadTotal property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/downloadTotal"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: downloadTotal property"
short-title: downloadTotal
slug: Web/API/BackgroundFetchRegistration/downloadTotal
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.downloadTotal
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`downloadTotal`** از رابط {{domxref("BackgroundFetchRegistration")}} اندازه کل این دانلود را به بایت برمی‌گرداند. این مقدار هنگام ثبت واکشی پس‌زمینه تنظیم می‌شود، یا اگر تنظیم نشده باشد `0` است.

## مقدار

یک {{jsxref("Number")}}.

## مثال‌ها

لاگ کردن این ویژگی در کنسول اندازه کل این دانلود را به بایت برمی‌گرداند.

```js
console.log(bgFetch.downloadTotal);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}