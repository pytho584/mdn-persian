---
title: "BackgroundFetchRegistration"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchRegistration"
translated_by: "n8n + AI"
---

---
title: BackgroundFetchRegistration
slug: Web/API/BackgroundFetchRegistration
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

رابط **`BackgroundFetchRegistration`** از {{domxref('Background Fetch API','','',' ')}} یک واکشی پس‌زمینه‌ی منفرد را نشان می‌دهد.

یک نمونه از `BackgroundFetchRegistration` توسط متدهای {{domxref("BackgroundFetchManager.fetch()")}} یا {{domxref("BackgroundFetchManager.get()")}} بازگردانده می‌شود و بنابراین سازنده‌ای ندارد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("BackgroundFetchRegistration.id")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای شامل شناسه‌ی واکشی پس‌زمینه.
- {{domxref("BackgroundFetchRegistration.uploadTotal")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : عددی ({{jsxref("Number")}}) شامل تعداد کل بایت‌هایی که باید بارگذاری شوند.
- {{domxref("BackgroundFetchRegistration.uploaded")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : عددی ({{jsxref("Number")}}) شامل اندازه به بایت که با موفقیت ارسال شده، در ابتدا `0`.
- {{domxref("BackgroundFetchRegistration.downloadTotal")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : عددی ({{jsxref("Number")}}) شامل اندازه کل این دانلود به بایت. این مقدار هنگام ثبت واکشی پس‌زمینه تنظیم شده است، یا `0`.
- {{domxref("BackgroundFetchRegistration.downloaded")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : عددی ({{jsxref("Number")}}) شامل اندازه به بایت که دانلود شده است، در ابتدا `0`.
- {{domxref("BackgroundFetchRegistration.result")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : در ابتدا یک رشته‌ی خالی بازمی‌گرداند، پس از تکمیل، یا رشته‌ی `"success"` یا `"failure"`.
- {{domxref("BackgroundFetchRegistration.failureReason")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای با مقداری که دلیل شکست واکشی پس‌زمینه را نشان می‌دهد. می‌تواند یکی از مقادیر زیر باشد: `""`، `"aborted"`، `"bad-status"`، `"fetch-error"`، `"quota-exceeded"`، `"download-total-exceeded"`.
- {{domxref("BackgroundFetchRegistration.recordsAvailable")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{jsxref("Boolean")}} که نشان می‌دهد پرچم `recordsAvailable` تنظیم شده است یا خیر.

## روش‌های نمونه

_همچنین روش‌های والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("BackgroundFetchRegistration.abort()")}} {{Experimental_Inline}}
  - : واکشی پس‌زمینه را لغو می‌کند. یک {{jsxref("Promise")}} بازمی‌گرداند که با `true` حل می‌شود اگر واکشی با موفقیت لغو شده باشد.
- {{domxref("BackgroundFetchRegistration.match()")}} {{Experimental_Inline}}
  - : یک شیء {{domxref("BackgroundFetchRecord")}} را بازمی‌گرداند که اولین تطابق با آرگومان‌ها است.
- {{domxref("BackgroundFetchRegistration.matchAll()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که با آرایه‌ای از اشیاء {{domxref("BackgroundFetchRecord")}} شامل درخواست‌ها و پاسخ‌ها حل می‌شود.

## رویدادها

_همچنین رویدادهای والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

برای گوش دادن به این رویدادها از {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا با اختصاص یک شنونده‌ی رویداد به ویژگی `oneventname` این رابط.

- {{domxref("BackgroundFetchRegistration/progress_event", "progress")}} {{Experimental_Inline}}
  - : زمانی که تغییری در هر یک از ویژگی‌های زیر رخ دهد، فعال می‌شود: {{domxref("BackgroundFetchRegistration.uploaded", "uploaded")}}، {{domxref("BackgroundFetchRegistration.downloaded", "downloaded")}}، {{domxref("BackgroundFetchRegistration.result", "result")}} یا {{domxref("BackgroundFetchRegistration.failureReason", "failureReason")}}.

## نمونه‌ها

کد زیر یک `BackGroundFetchRegistration` به‌عنوان `bgFetch` با `id` برابر با `"my-fetch"` ایجاد می‌کند.

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const bgFetch = await swReg.backgroundFetch.fetch(
    "my-fetch",
    ["/ep-5.mp3", "ep-5-artwork.jpg"],
    {
      title: "Episode 5: Interesting things.",
      icons: [
        {
          sizes: "300x300",
          src: "/ep-5-icon.png",
          type: "image/png",
        },
      ],
      downloadTotal: 60 * 1024 * 1024,
    },
  );
});
```

ثبت {{domxref("BackgroundFetchRegistration.id","id")}} در کنسول، `"my-fetch"` را برمی‌گرداند.

```js
console.log(bgFetch.id); // "my-fetch"
```

متد {{domxref("BackgroundFetchRegistration.match","match()")}} می‌تواند برای یافتن یک {{domxref("BackgroundFetchRecord")}} خاص از میان آن‌هایی که بخشی از ثبت هستند استفاده شود.

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

## سازگاری مرورگر

{{Compat}}