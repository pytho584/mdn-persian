---
title: "BluetoothRemoteGATTService"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTService"
translated_by: "n8n + AI"
---

---
title: BluetoothRemoteGATTService
slug: Web/API/BluetoothRemoteGATTService
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTService
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط `BluetoothRemoteGATTService` در [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) نمایانگر سرویسی است که توسط سرور GATT ارائه می‌شود، شامل یک دستگاه، فهرستی از سرویس‌های ارجاع‌شده، و فهرستی از ویژگی‌های این سرویس.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("BluetoothRemoteGATTService.device")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : اطلاعاتی درباره یک دستگاه بلوتوث از طریق یک نمونه از {{domxref("BluetoothDevice")}} برمی‌گرداند.
- {{domxref("BluetoothRemoteGATTService.isPrimary")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد این سرویس اولیه است یا ثانویه.
- {{domxref("BluetoothRemoteGATTService.uuid")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته برمی‌گرداند که UUID این سرویس را نشان می‌دهد.

## متدهای نمونه

- {{domxref("BluetoothRemoteGATTService.getCharacteristic()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} به یک نمونه از {{domxref("BluetoothRemoteGATTCharacteristic")}} برای یک شناسه یکتای جهانی (UUID) معین برمی‌گرداند.
- {{domxref("BluetoothRemoteGATTService.getCharacteristics()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} به یک {{jsxref("Array")}} از نمونه‌های {{domxref("BluetoothRemoteGATTCharacteristic")}} برای یک شناسه یکتای جهانی (UUID) اختیاری برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}