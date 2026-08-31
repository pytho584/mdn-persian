---
title: "BluetoothRemoteGATTService: getCharacteristic() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTService/getCharacteristic"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTService: getCharacteristic() method"
short-title: getCharacteristic()
slug: Web/API/BluetoothRemoteGATTService/getCharacteristic
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTService.getCharacteristic
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothGATTService.getCharacteristic()`** یک {{jsxref("Promise")}} به یک نمونه از {{domxref("BluetoothRemoteGATTCharacteristic")}} برای یک شناسه یکتای جهانی (UUID) برمی‌گرداند.

## Syntax

```js-nolint
getCharacteristic(characteristic)
```

### پارامترها

- `characteristic`
  - : UUID یک مشخصه، برای مثال `'00002a37-0000-1000-8000-00805f9b34fb'` برای مشخصه اندازه‌گیری ضربان قلب (Heart Rate Measurement).

### مقدار برگشتی

یک {{jsxref("Promise")}} به یک نمونه از {{domxref("BluetoothRemoteGATTCharacteristic")}}

## Specifications

{{Specifications}}

## سازگاری مرورگر

{{Compat}}