---
title: "BluetoothRemoteGATTServer: getPrimaryService() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTServer/getPrimaryService"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTServer: getPrimaryService() method"
short-title: getPrimaryService()
slug: Web/API/BluetoothRemoteGATTServer/getPrimaryService
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTServer.getPrimaryService
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTServer.getPrimaryService()`** یک قول (Promise) را به سرویس اصلی {{domxref("BluetoothRemoteGATTService")}} که توسط دستگاه بلوتوث برای یک UUID سرویس بلوتوث مشخص ارائه می‌شود، برمی‌گرداند.

## Syntax

```js-nolint
getPrimaryService(bluetoothServiceUUID)
```

### پارامترها

- `bluetoothServiceUUID`
  - : یک شناسه منحصربه‌فرد جهانی سرویس بلوتوث برای یک دستگاه مشخص، که می‌تواند یک UUID 128-بیتی، یک نام مستعار UUID 16-بیتی یا 32-بیتی، یا یک رشته از فهرست کلیدهای [سرویس‌های اختصاصی GATT](https://github.com/WebBluetoothCG/registries/blob/master/gatt_assigned_services.txt) باشد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء {{domxref("BluetoothRemoteGATTService")}} حل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}