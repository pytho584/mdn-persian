---
title: "BluetoothRemoteGATTCharacteristic: getDescriptor() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic/getDescriptor"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTCharacteristic: getDescriptor() method"
short-title: getDescriptor()
slug: Web/API/BluetoothRemoteGATTCharacteristic/getDescriptor
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic.getDescriptor
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTCharacteristic.getDescriptor()`** یک {{jsxref("Promise")}} برمی‌گرداند که به اولین {{domxref("BluetoothRemoteGATTDescriptor")}} برای یک UUID توصیف‌گر مشخص، حل می‌شود.

## نحو

```js-nolint
getDescriptor(bluetoothDescriptorUUID)
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به اولین {{domxref("BluetoothRemoteGATTDescriptor")}} حل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}