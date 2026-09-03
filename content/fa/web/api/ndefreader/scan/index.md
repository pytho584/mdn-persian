---
title: "NDEFReader: scan() method"
short-title: scan()
slug: Web/API/NDEFReader/scan
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NDEFReader.scan
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

متد `scan()` در رابط {{DOMxRef("NDEFReader")}} دستگاه خواننده را فعال می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند که یا زمانی که یک عملیات خواندن تگ NFC زمان‌بندی می‌شود با موفقیت resolve می‌شود و یا در صورت بروز خطای سخت‌افزاری یا مجوز reject می‌شود. اگر مجوز «nfc» قبلاً داده نشده باشد، این متد یک درخواست مجوز (permission prompt) را فعال می‌کند.

## Syntax

```js-nolint
scan(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `signal`
      - : یک {{DOMxRef("AbortSignal")}} که امکان لغو این عملیات `scan()` را فراهم می‌کند.

### Return value

یک {{JSxRef("Promise")}} که بلافاصله پس از زمان‌بندی عملیات خواندن برای آداپتور NFC resolve می‌شود.

### Exceptions

این متد استثنا پرتاب نمی‌کند؛ در عوض، promise برگشتی را reject می‌کند و یک {{domxref("DOMException")}} ارسال می‌کند که `name` آن یکی از موارد زیر است:

- `AbortError` {{domxref("DOMException")}}
  - : اگر عملیات scan با {{DOMxRef("AbortSignal")}} ارسال‌شده در آرگومان `options` لغو شده باشد، برگردانده می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر از قبل یک scan در حال انجام باشد، برگردانده می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر مجوز این عملیات رد شده باشد، برگردانده می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر هیچ آداپتور NFC سازگار با Web NFC وجود نداشته باشد یا اتصال برقرار نشود، برگردانده می‌شود.

## Examples

### Handle scanning errors

این مثال نشان می‌دهد که وقتی promise مربوط به scan رد می‌شود و `readingerror` رخ می‌دهد، چه اتفاقی می‌افتد.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}