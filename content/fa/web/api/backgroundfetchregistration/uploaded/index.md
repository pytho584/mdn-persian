---
title: "BackgroundFetchRegistration: uploaded property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/uploaded"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: uploaded property"
short-title: uploaded
slug: Web/API/BackgroundFetchRegistration/uploaded
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.uploaded
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی **`uploaded`** فقط‌خواندنی از رابط {{domxref("BackgroundFetchRegistration")}} اندازه‌ای را که با موفقیت ارسال شده، بر حسب بایت برمی‌گرداند؛ در ابتدا `0`.

اگر مقدار این ویژگی تغییر کند، رویداد [progress](/en-US/docs/Web/API/BackgroundFetchRegistration/progress_event) در شیء {{domxref("BackgroundFetchRegistration")}} مرتبط رخ می‌دهد.

## مقدار

یک {{jsxref("Number")}}.

## مثال‌ها

ثبت این ویژگی در کنسول، تعداد بایت‌های آپلودشده را برمی‌گرداند.

```js
console.log(bgFetch.uploaded);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}