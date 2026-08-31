---
title: "Bluetooth: getAvailability() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth/getAvailability"
translated_by: "n8n + AI"
---

---
title: "Bluetooth: getAvailability() method"
short-title: getAvailability()
slug: Web/API/Bluetooth/getAvailability
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Bluetooth.getAvailability
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{securecontext_header}}

روش **`getAvailability()`** از رابط {{DOMxRef("Bluetooth")}} به‌صورت _اسمی_ مقدار `true` را برمی‌گرداند اگر عامل کاربر بتواند بلوتوث را پشتیبانی کند (زیرا دستگاه دارای آداپتور بلوتوث است) و در غیر این صورت `false` را برمی‌گرداند.

کلمه «اسمی» به این دلیل استفاده می‌شود که اگر اجازه استفاده از Web Bluetooth API توسط مجوز [`Permissions-Policy: bluetooth`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/bluetooth) رد شود، این روش همیشه `false` برمی‌گرداند.
علاوه بر این، کاربر می‌تواند مرورگر خود را طوری پیکربندی کند که حتی اگر مرورگر دارای آداپتور بلوتوث عملیاتی باشد، فراخوانی `getAvailability()` مقدار `false` برگرداند و بالعکس. این مقدار تنظیمات در صورت مسدود شدن دسترسی توسط مجوز نادیده گرفته می‌شود.

حتی اگر `getAvailability()` مقدار `true` برگرداند و دستگاه واقعاً دارای آداپتور بلوتوث باشد، لزوماً به این معنی نیست که فراخوانی {{DOMxRef("Bluetooth.requestDevice","navigator.bluetooth.requestDevice()")}} با یک {{DOMxRef("BluetoothDevice")}} حل خواهد شد.
ممکن است آداپتور بلوتوث روشن نباشد و ممکن است کاربر هنگام درخواست، اجازه استفاده از API را رد کند.

## Syntax

```js-nolint
getAvailability()
```

### Parameters

هیچ.

### Return value

یک {{JSxRef("Promise")}} که با یک {{JSxRef("Boolean")}} حل می‌شود.

{{JSxRef("Promise")}} با مقدار `false` حل می‌شود اگر دسترسی توسط [`Permissions-Policy: bluetooth`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/bluetooth) رد شده باشد، اگر کاربر مرورگر را به‌گونه‌ای پیکربندی کرده باشد که همیشه `false` برگرداند، یا اگر دستگاه دارای آداپتور بلوتوث نباشد.
در غیر این صورت با `true` حل می‌شود.

### Exceptions

هیچ.

## Examples

قطعه کد زیر پیامی را در کنسول چاپ می‌کند که مشخص می‌کند آیا بلوتوث توسط دستگاه پشتیبانی می‌شود یا نه:

```js
navigator.bluetooth.getAvailability().then((available) => {
  if (available) {
    console.log("This device supports Bluetooth!");
  } else {
    console.log("Doh! Bluetooth is not supported");
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}