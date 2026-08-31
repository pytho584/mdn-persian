---
title: "BluetoothRemoteGATTCharacteristic: getDescriptors() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic/getDescriptors"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTCharacteristic: getDescriptors() method"
short-title: getDescriptors()
slug: Web/API/BluetoothRemoteGATTCharacteristic/getDescriptors
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic.getDescriptors
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTCharacteristic.getDescriptors()`** یک {{jsxref("Promise")}} برمی‌گرداند که به یک {{jsxref("Array")}} از همه اشیاء {{domxref("BluetoothRemoteGATTDescriptor")}} برای یک UUID توصیفگر معین حل می‌شود.

## نحو

```js-nolint
getDescriptors(bluetoothDescriptorUUID)
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک {{jsxref("Array")}} از اشیاء {{domxref("BluetoothRemoteGATTDescriptor")}} حل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}