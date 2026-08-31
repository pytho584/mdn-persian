---
title: "BluetoothRemoteGATTService: getCharacteristics() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTService/getCharacteristics"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTService: getCharacteristics() method"
short-title: getCharacteristics()
slug: Web/API/BluetoothRemoteGATTService/getCharacteristics
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTService.getCharacteristics
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothGATTService.getCharacteristics()`** یک {{jsxref("Promise")}} را به فهرستی از نمونه‌های {{domxref("BluetoothRemoteGATTCharacteristic")}} برای یک شناسه یکتای جهانی (UUID) مشخص بازمی‌گرداند.

## نحو

```js-nolint
getCharacteristics(characteristics)
```

### پارامترها

- `characteristics`
  - : UUID یک مشخصه، به عنوان مثال `'00002a37-0000-1000-8000-00805f9b34fb'` برای مشخصه اندازه‌گیری ضربان قلب.

### مقدار بازگشتی

یک {{jsxref("Promise")}} به یک {{jsxref("Array")}} از نمونه‌های {{domxref("BluetoothRemoteGATTCharacteristic")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}