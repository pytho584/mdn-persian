---
title: "BluetoothUUID: getService() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothUUID/getService_static"
translated_by: "n8n + AI"
---

---
title: "BluetoothUUID: getService() static method"
short-title: getService()
slug: Web/API/BluetoothUUID/getService_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.BluetoothUUID.getService_static
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}

متد ایستا **`getService()`** در رابط {{domxref("BluetoothUUID")}} یک UUID برمی‌گرداند که نشان‌دهنده یک سرویس ثبت‌شده است، زمانی که یک نام یا نام مستعار UUID ۱۶ یا ۳۲ بیتی به آن داده شود.

## نحو

```js-nolint
BluetoothUUID.getService(name)
```

### پارامترها

- `name`
  - : رشته‌ای شامل نام سرویس.

### مقدار بازگشتی

یک UUID ۱۲۸ بیتی.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `name` در رجیستری وجود نداشته باشد پرتاب می‌شود.

## مثال‌ها

در مثال زیر، UUID نشان‌دهنده سرویس به نام `device_information` برگردانده شده و در کنسول چاپ می‌شود.

```js
let result = BluetoothUUID.getService("device_information");
console.log(result); // "0000180a-0000-1000-8000-00805f9b34fb"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}