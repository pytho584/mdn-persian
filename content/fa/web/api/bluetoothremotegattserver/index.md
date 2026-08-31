---
title: "BluetoothRemoteGATTServer"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTServer"
translated_by: "n8n + AI"
---

---
title: BluetoothRemoteGATTServer
slug: Web/API/BluetoothRemoteGATTServer
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTServer
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`BluetoothRemoteGATTServer`** از [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) یک سرور GATT را روی یک دستگاه از راه دور نمایش می‌دهد.

## خاصیت‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTServer.connected")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک مقدار بولی که تا زمانی که این محیط اجرای اسکریپت به `this.device` متصل است، `true` برمی‌گرداند. ممکن است در حالی که عامل کاربر به صورت فیزیکی متصل است، `false` باشد.
- {{DOMxRef("BluetoothRemoteGATTServer.device")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک ارجاع به {{DOMxRef("BluetoothDevice")}} که سرور را اجرا می‌کند.

## روش‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTServer.connect()")}} {{Experimental_Inline}}
  - : باعث می‌شود محیط اجرای اسکریپت به `this.device` متصل شود.
- {{DOMxRef("BluetoothRemoteGATTServer.disconnect()")}} {{Experimental_Inline}}
  - : باعث می‌شود محیط اجرای اسکریپت از `this.device` قطع اتصال کند.
- {{DOMxRef("BluetoothRemoteGATTServer.getPrimaryService()")}} {{Experimental_Inline}}
  - : یک پرامیس به {{DOMxRef("BluetoothRemoteGATTService")}} اولیه ارائه‌شده توسط دستگاه بلوتوث برای یک `BluetoothServiceUUID` مشخص برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTServer.getPrimaryServices()")}} {{Experimental_Inline}}
  - : یک پرامیس به فهرستی از اشیاء {{DOMxRef("BluetoothRemoteGATTService")}} اولیه ارائه‌شده توسط دستگاه بلوتوث برای یک `BluetoothServiceUUID` مشخص برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}