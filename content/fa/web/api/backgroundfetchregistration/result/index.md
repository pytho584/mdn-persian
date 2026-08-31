---
title: "BackgroundFetchRegistration: result property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/result"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: result property"
short-title: result
slug: Web/API/BackgroundFetchRegistration/result
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.result
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`result`** از رابط {{domxref("BackgroundFetchRegistration")}} یک رشته برمی‌گرداند که نشان می‌دهد واکشی پس‌زمینه موفقیت‌آمیز بوده یا ناموفق.

اگر مقدار این ویژگی تغییر کند، رویداد [progress](/en-US/docs/Web/API/BackgroundFetchRegistration/progress_event) در شیء {{domxref("BackgroundFetchRegistration")}} مرتبط فعال می‌شود.

## مقدار

یکی از رشته‌های زیر:

- `""`
  - : واکشی فعال است بنابراین نتیجه‌ای وجود ندارد.
- `"success"`
  - : واکشی پس‌زمینه موفقیت‌آمیز بود.
- `"failure"`
  - : واکشی پس‌زمینه ناموفق بود. این تنها زمانی ظاهر می‌شود که مرورگر قابلیت تلاش مجدد را نداشته باشد.

## مثال‌ها

ثبت این ویژگی در کنسول یک رشته را برمی‌گرداند که وضعیت را نشان می‌دهد، یا در صورت فعال بودن واکشی، یک رشته خالی.

```js
console.log(bgFetch.result);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}