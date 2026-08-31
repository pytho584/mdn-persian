---
title: "BackgroundFetchRegistration: progress event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration/progress_event"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchRegistration: progress event"
short-title: progress
slug: Web/API/BackgroundFetchRegistration/progress_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.progress_event
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رویداد **`progress`** از رابط {{domxref("BackgroundFetchRegistration")}} هنگامی که واکشی پس‌زمینه‌ی مرتبط پیشرفت می‌کند، صادر می‌شود.

در عمل، این رویداد زمانی صادر می‌شود که هر یک از ویژگی‌های زیر مقدار جدیدی بازگردانند:

- {{domxref("BackgroundFetchRegistration.uploaded", "uploaded")}},
- {{domxref("BackgroundFetchRegistration.downloaded", "downloaded")}},
- {{domxref("BackgroundFetchRegistration.result", "result")}}, یا
- {{domxref("BackgroundFetchRegistration.failureReason", "failureReason")}}.

## نحو

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("progress", (event) => { })

onprogress = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی بدون ویژگی‌های اضافه‌شده.

## مثال

مثال زیر نشان می‌دهد که چگونه پیشرفت یک دانلود را ثبت کنید. کد ابتدا بررسی می‌کند که هنگام ثبت واکشی پس‌زمینه، `downloadTotal` ارائه شده باشد. سپس از آن برای محاسبه درصد بر اساس ویژگی `downloaded` استفاده می‌شود.

```js
bgFetch.addEventListener("progress", () => {
  if (!bgFetch.downloadTotal) return;
  const percent = Math.round(
    (bgFetch.downloaded / bgFetch.downloadTotal) * 100,
  );
  console.log(`Download progress: ${percent}%`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}