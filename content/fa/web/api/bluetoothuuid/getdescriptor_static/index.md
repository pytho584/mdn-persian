---
title: "BluetoothUUID: getDescriptor() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothUUID/getDescriptor_static"
translated_by: "n8n + AI"
short-title: getDescriptor()
slug: Web/API/BluetoothUUID/getDescriptor_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.BluetoothUUID.getDescriptor_static
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}

متد استاتیک **`getDescriptor()`** از رابط {{domxref("BluetoothUUID")}} یک UUID را که نمایانگر یک توصیف‌کننده (descriptor) ثبت‌شده است، هنگام دریافت یک نام یا نام مستعار UUID 16 یا 32 بیتی، برمی‌گرداند.

## نحو (Syntax)

```js-nolint
BluetoothUUID.getDescriptor(name)
```

### پارامترها

- `name`
  - : یک رشته شامل نام توصیف‌کننده.

### مقدار بازگشتی

یک UUID 128 بیتی.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر `name` در رجیستری وجود نداشته باشد، پرتاب می‌شود.

## مثال‌ها

در مثال زیر، UUID نمایانگر توصیف‌کننده با نام `time_trigger_setting` برگردانده شده و در کنسول چاپ می‌شود.

```js
let result = BluetoothUUID.getDescriptor("time_trigger_setting");
console.log(result); // "0000290e-0000-1000-8000-00805f9b34fb"
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}