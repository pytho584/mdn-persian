---
title: "NDEFReader: reading event"
short-title: reading
slug: Web/API/NDEFReader/reading_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.NDEFReader.reading_event
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

رویداد `reading` از رابط {{DOMxRef("NDEFReader")}} هرگاه یک خوانش جدید از دستگاه‌های NFC سازگار (مانند برچسب‌های NFC که از NDEF پشتیبانی می‌کنند) در دسترس باشد و این دستگاه‌ها در میدان القای مغناطیسی خواننده قرار داشته باشند، فعال می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("reading", (event) => { })

onreading = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

مثال زیر نحوه پردازش رویدادها را با استفاده از هر دو کنترل‌کننده رویداد `onreading` و `onreadingerror` نشان می‌دهد.

```js
const ndef = new NDEFReader();
ndef
  .scan()
  .then(() => {
    console.log("Scan started successfully.");
    ndef.onreadingerror = (event) => {
      console.log(
        "Error! Cannot read data from the NFC tag. Try a different one?",
      );
    };
    ndef.onreading = (event) => {
      console.log("NDEF message read.");
    };
  })
  .catch((error) => {
    console.log(`Error! Scan failed to start: ${error}.`);
  });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{DOMxRef("NDEFReader.readingerror_event", "readingerror")}}