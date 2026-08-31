---
title: "BluetoothUUID"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothUUID"
translated_by: "n8n + AI"
---

---
title: BluetoothUUID
slug: Web/API/BluetoothUUID
page-type: web-api-interface
browser-compat: api.BluetoothUUID
---

{{APIRef("Bluetooth API")}}

رابط **`BluetoothUUID`** از [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) راهی برای جستجوی مقادیر شناسه یکتای جهانی (UUID) بر اساس نام در [ثبت](https://www.bluetooth.com/specifications/assigned-numbers/) نگهداری شده توسط Bluetooth SIG فراهم می‌کند.

## توضیحات

یک رشته UUID یک UUID 128 بیتی است، برای مثال `00001818-0000-1000-8000-00805f9b34fb`. ثبث Bluetooth شامل لیست‌هایی از توصیف‌گرها، خدمات و ویژگی‌های شناسایی شده توسط این UUIDها به همراه یک نام مستعار 16 یا 32 بیتی و یک نام است.

رابط `BluetoothUUID` روش‌هایی برای بازیابی این UUIDهای 128 بیتی فراهم می‌کند.

## روش‌های استاتیک

- [`BluetoothUUID.canonicalUUID()`](/en-US/docs/Web/API/BluetoothUUID/canonicalUUID_static) {{Experimental_Inline}}
  - : UUID 128 بیتی را زمانی که نام مستعار UUID 16 یا 32 بیتی به آن داده شود، برمی‌گرداند.
- [`BluetoothUUID.getCharacteristic()`](/en-US/docs/Web/API/BluetoothUUID/getCharacteristic_static) {{Experimental_Inline}}
  - : UUID 128 بیتی نماینده یک ویژگی ثبت‌شده را زمانی که یک نام یا نام مستعار UUID 16 یا 32 بیتی به آن داده شود، برمی‌گرداند.
- [`BluetoothUUID.getDescriptor()`](/en-US/docs/Web/API/BluetoothUUID/getDescriptor_static) {{Experimental_Inline}}
  - : UUID نماینده یک توصیف‌گر ثبت‌شده را زمانی که یک نام یا نام مستعار UUID 16 یا 32 بیتی به آن داده شود، برمی‌گرداند.
- [`BluetoothUUID.getService()`](/en-US/docs/Web/API/BluetoothUUID/getService_static) {{Experimental_Inline}}
  - : UUID نماینده یک سرویس ثبت‌شده را زمانی که یک نام یا نام مستعار UUID 16 یا 32 بیتی به آن داده شود، برمی‌گرداند.

## مثال‌ها

در مثال زیر UUID نماینده سرویس به نام `device_information` برگردانده شده و در کنسول چاپ می‌شود.

```js
let result = BluetoothUUID.getService("device_information");
console.log(result); // "0000180a-0000-1000-8000-00805f9b34fb"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}