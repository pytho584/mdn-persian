---
title: NDEFReader
slug: Web/API/NDEFReader
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NDEFReader
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

رابط **`NDEFReader`** متعلق به [Web NFC API](/en-US/docs/Web/API/Web_NFC_API) برای خواندن و نوشتنِ داده روی دستگاه‌های سازگار با NFC، مانند تگ‌های NFC که از NDEF پشتیبانی می‌کنند، به کار می‌رود؛ به شرط آنکه این دستگاه‌ها در میدان القای مغناطیسیِ خواننده قرار داشته باشند.

{{InheritanceDiagram}}

## سازنده

- {{DOMxRef("NDEFReader.NDEFReader", "NDEFReader()")}} {{Experimental_Inline}}
  - : یک شیء `NDEFReader` جدید برمی‌گرداند.

## متدهای نمونه

رابطِ `NDEFReader` متدهای {{domxref("EventTarget")}} — رابط والد خود — را به ارث می‌برد.

- {{DOMxRef("NDEFReader.scan", "NDEFReader.scan()")}} {{Experimental_Inline}}
  - : یک دستگاه خواننده را فعال می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند. این Promise زمانی resolve می‌شود که عملیات خواندنِ تگ NFC برنامه‌ریزی شده باشد و در صورت بروز خطای سخت‌افزاری یا خطای مجوز، reject می‌شود. اگر مجوز «nfc» پیشتر صادر نشده باشد، این متد اعلان درخواست مجوز را نمایش می‌دهد.
- {{DOMxRef("NDEFReader.write", "NDEFReader.write()")}} {{Experimental_Inline}}
  - : تلاش می‌کند یک پیام NDEF را روی یک تگ بنویسد و یک {{jsxref("Promise")}} برمی‌گرداند که یا پس از نوشته‌شدن پیام روی تگ resolve می‌شود و یا در صورت بروز خطای سخت‌افزاری یا خطای مجوز reject می‌شود. اگر مجوز «nfc» پیشتر صادر نشده باشد، این متد اعلان درخواست مجوز را نمایش می‌دهد.

## رویدادها

_رویدادها را از والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

- {{DOMxRef("NDEFReader.reading_event", "reading")}} {{Experimental_Inline}}
  - : وقتی یک خوانش جدید از دستگاه‌های NFC سازگار در دسترس باشد، این رویداد رخ می‌دهد.
- {{DOMxRef("NDEFReader.readingerror_event", "readingerror")}} {{Experimental_Inline}}
  - : وقتی یک تگ در مجاورت دستگاهِ خواننده قرار گرفته باشد اما امکان خواندنش نباشد، این رویداد رخ می‌دهد.

## مثال‌ها

### مدیریت خوانش‌های اولیه هنگام نوشتن

مثال زیر نشان می‌دهد که چگونه می‌توان بین یک مدیریت‌کنندهٔ عمومیِ خوانش و مدیریت‌کننده‌ای که به‌طور خاص برای یک نوشتنِ منفرد استفاده می‌شود، هماهنگی ایجاد کرد. برای نوشتن، ابتدا باید یک تگ پیدا و خوانده شود؛ این کار به شما امکان می‌دهد بررسی کنید که آیا این تگ واقعاً همان تگی است که می‌خواهید روی آن بنویسید. به همین دلیل توصیه می‌شود `write()` را از داخل یک رویدادِ خوانش فراخوانی کنید.

```js
const ndef = new NDEFReader();
let ignoreRead = false;

ndef.onreading = (event) => {
  if (ignoreRead) {
    return; // write pending, ignore read.
  }

  console.log("We read a tag, but not during pending write!");
};

function write(data) {
  ignoreRead = true;
  return new Promise((resolve, reject) => {
    ndef.addEventListener(
      "reading",
      (event) => {
        // Check if we want to write to this tag, or reject.
        ndef
          .write(data)
          .then(resolve, reject)
          .finally(() => (ignoreRead = false));
      },
      { once: true },
    );
  });
}

await ndef.scan();
try {
  await write("Hello World");
  console.log("We wrote to a tag!");
} catch (err) {
  console.error("Something went wrong", err);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}