---
title: "BackgroundFetchRegistration: downloaded property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/downloaded"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: downloaded property"
short-title: downloaded
slug: Web/API/BackgroundFetchRegistration/downloaded
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.downloaded
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`downloaded`** از رابط {{domxref("BackgroundFetchRegistration")}} اندازهٔ دانلودشده را به بایت برمی‌گرداند که در ابتدا `0` است.

اگر مقدار این ویژگی تغییر کند، رویداد [progress](/en-US/docs/Web/API/BackgroundFetchRegistration/progress_event) در شیء {{domxref("BackgroundFetchRegistration")}} مرتبط فعال می‌شود.

## مقدار

یک {{jsxref("Number")}}.

## مثال‌ها

ثبت این ویژگی در کنسول، تعداد بایت‌های دانلودشده را برمی‌گرداند.

```js
console.log(bgFetch.downloaded);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}