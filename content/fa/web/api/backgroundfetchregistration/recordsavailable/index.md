---
title: "BackgroundFetchRegistration: recordsAvailable property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/recordsAvailable"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: recordsAvailable property"
short-title: recordsAvailable
slug: Web/API/BackgroundFetchRegistration/recordsAvailable
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.recordsAvailable
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقطخواندنی **`recordsAvailable`** از رابط {{domxref("BackgroundFetchRegistration")}} در صورتی مقدار `true` را برمی‌گرداند که درخواست‌ها و پاسخ‌هایی برای دسترسی وجود داشته باشد. اگر این مقدار `false` برگردد، {{domxref("BackgroundFetchRegistration.match()","match()")}} و {{domxref("BackgroundFetchRegistration.matchAll()","matchAll()")}} قابل استفاده نیستند.

## مقدار

یک {{jsxref("Boolean")}}.

## مثال‌ها

ثبت این ویژگی در کنسول، مقدار `true` یا `false` را برمی‌گرداند که نشان می‌دهد آیا رکوردهایی وجود دارد.

```js
console.log(bgFetch.recordsAvailable);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}