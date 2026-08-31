---
title: "BluetoothDevice"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothDevice"
translated_by: "n8n + AI"
---

---
title: BluetoothDevice
slug: Web/API/BluetoothDevice
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothDevice
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط `BluetoothDevice` از [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) یک دستگاه بلوتوث را در یک محیط اجرای اسکریپت مشخص نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{DOMxRef("BluetoothDevice.id")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک رشته که به طور یکتا یک دستگاه را شناسایی می‌کند.
- {{DOMxRef("BluetoothDevice.name")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک رشته که یک نام قابل خواندن برای انسان برای دستگاه ارائه می‌دهد.
- {{DOMxRef("BluetoothDevice.gatt")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک ارجاع به {{DOMxRef("BluetoothRemoteGATTServer")}} دستگاه.

## روش‌های نمونه

- {{DOMxRef("BluetoothDevice.watchAdvertisements()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} که به `undefined` حل می‌شود یا در صورت عدم امکان نمایش تبلیغات به هر دلیلی با یک خطا رد می‌شود.
- {{DOMxRef("BluetoothDevice.forget()")}} {{Experimental_Inline}}
  - : راهی برای صفحه فراهم می‌کند تا دسترسی به دستگاهی که کاربر اجازه دسترسی به آن را داده است لغو کند.

## رویدادها

به این رویدادها با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

- {{DOMxRef("BluetoothDevice/gattserverdisconnected_event", "gattserverdisconnected")}} {{experimental_inline}}
  - : زمانی که یک اتصال GATT فعال از دست می‌رود، روی یک دستگاه فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}