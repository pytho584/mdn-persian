---
title: "NDEFReader: readingerror event"
short-title: readingerror
slug: Web/API/NDEFReader/readingerror_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.NDEFReader.readingerror_event
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

رویداد `readingerror` از رابط {{DOMxRef("NDEFReader")}} هرگاه خطایی در هنگام خواندن برچسب‌های NFC رخ دهد، به‌عنوان مثال زمانی که برچسب‌ها از میدان القای مغناطیسی خواننده خارج می‌شوند، فعال می‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("readingerror", (event) => { })

onreadingerror = (event) => { }
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

## سازگاری مرورگر

{{Compat}}