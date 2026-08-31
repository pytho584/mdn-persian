---
title: "BluetoothRemoteGATTServer: getPrimaryServices() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTServer/getPrimaryServices"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTServer: getPrimaryServices() method"
short-title: getPrimaryServices()
slug: Web/API/BluetoothRemoteGATTServer/getPrimaryServices
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTServer.getPrimaryServices
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **BluetoothRemoteGATTServer.getPrimaryServices()** یک وعده (Promise) به فهرستی از اشیاء اصلی {{domxref("BluetoothRemoteGATTService")}} که توسط دستگاه بلوتوث برای یک `BluetoothServiceUUID` مشخص ارائه می‌شوند، برمی‌گرداند.

## نحو

```js-nolint
getPrimaryServices(bluetoothServiceUUID)
```

### پارامترها

- `bluetoothServiceUUID`
  - : یک شناسه یکتای جهانی سرویس بلوتوث برای دستگاه مشخص.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به فهرستی از اشیاء {{domxref("BluetoothRemoteGATTService")}} تبدیل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}