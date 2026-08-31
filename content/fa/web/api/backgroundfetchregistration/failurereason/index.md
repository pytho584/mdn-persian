---
title: "BackgroundFetchRegistration: failureReason property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/failureReason"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: failureReason property"
short-title: failureReason
slug: Web/API/BackgroundFetchRegistration/failureReason
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.failureReason
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`failureReason`** از رابط {{domxref("BackgroundFetchRegistration")}} رشته‌ای را برمی‌گرداند که مقدار آن نشان‌دهندهٔ دلیل شکست یک واکشی پس‌زمینه است.

اگر مقدار این ویژگی تغییر کند، رویداد [progress](/en-US/docs/Web/API/BackgroundFetchRegistration/progress_event) روی شیء {{domxref("BackgroundFetchRegistration")}} مرتبط فعال می‌شود.

## مقدار

یکی از رشته‌های زیر:

- `""`
  - واکشی پس‌زمینه کامل نشده است، یا با موفقیت انجام شده است.
- `"aborted"`
  - عملیات توسط کاربر لغو شد، یا {{domxref("BackgroundFetchRegistration.abort()","abort()")}} فراخوانی شد.
- `"bad-status"`
  - یک پاسخ دارای وضعیت ناموفق بود (وضعیتی خارج از بازهٔ ۲۰۰ تا ۲۹۹).
- `"fetch-error"`
  - یک واکشی به دلایل دیگری شکست خورد، برای مثال CORS یا خطای شبکه.
- `"quota-exceeded"`
  - در حین عملیات، سهمیه ذخیره‌سازی به پایان رسید.
- `"download-total-exceeded"`
  - `downloadTotal` ارائه‌شده بیش از حد شد. این مقدار هنگام ثبت واکشی پس‌زمینه تنظیم شده بود.

## مثال‌ها

ثبت این ویژگی در کنسول، دلیل شکست واکشی را چاپ می‌کند، یا اگر موفق یا هنوز کامل نشده باشد، یک رشته خالی چاپ می‌کند.

```js
console.log(bgFetch.failureReason);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}