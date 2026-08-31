---
title: BluetoothRemoteGATTDescriptor
slug: Web/API/BluetoothRemoteGATTDescriptor
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTDescriptor
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابطهٔ `BluetoothRemoteGATTDescriptor` در [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) یک توصیفگر GATT را فراهم می‌کند که اطلاعات بیشتری دربارهٔ مقدار یک مشخصه (characteristic) ارائه می‌دهد.

## ویژگی‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTDescriptor.characteristic")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : {{DOMxRef("BluetoothRemoteGATTCharacteristic")}} که این توصیفگر به آن تعلق دارد را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTDescriptor.uuid")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : UUID توصیفگر مشخصه را برمی‌گرداند، برای مثال `"00002902-0000-1000-8000-00805f9b34fb"` برای توصیفگر پیکربندی مشخصه کلاینت (Client Characteristic Configuration descriptor).
- {{DOMxRef("BluetoothRemoteGATTDescriptor.value")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار توصیفگرِ در حال حافظهٔ نهان (cached) را برمی‌گرداند. این مقدار وقتی به‌روزرسانی می‌شود که مقدار توصیفگر خوانده شود.

## روش‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTDescriptor.readValue()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که با یک {{JSxRef("ArrayBuffer")}} شامل یک کپی از ویژگی `value` (در صورت موجود بودن و پشتیبانی شدن) حل می‌شود. در غیر این صورت یک خطا ایجاد می‌کند.
- {{DOMxRef("BluetoothRemoteGATTDescriptor.writeValue()")}} {{Experimental_Inline}}
  - : ویژگی value را به بایت‌های موجود در یک {{JSxRef("ArrayBuffer")}} تنظیم می‌کند و یک {{JSxRef("Promise")}} برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}