---
title: "BluetoothRemoteGATTCharacteristic"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic"
translated_by: "n8n + AI"
---

---
title: BluetoothRemoteGATTCharacteristic
slug: Web/API/BluetoothRemoteGATTCharacteristic
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط `BluetoothRemoteGattCharacteristic` از [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) یک مشخصه GATT را نشان می‌دهد که یک عنصر داده پایه است که اطلاعات بیشتری درباره سرویس یک دستگاه جانبی فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTCharacteristic.service")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : {{DOMxRef("BluetoothRemoteGATTService")}} که این مشخصه به آن تعلق دارد را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.uuid")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته حاوی UUID مشخصه را برمی‌گرداند، برای مثال `'00002a37-0000-1000-8000-00805f9b34fb'` برای مشخصه اندازه‌گیری ضربان قلب.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.properties")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : ویژگی‌های این مشخصه را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.value")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار مشخصه ذخیره‌شده فعلی. این مقدار زمانی به‌روز می‌شود که مقدار مشخصه از طریق یک اعلان یا نشانه خوانده یا به‌روز شود.

## روش‌های نمونه

- {{DOMxRef("BluetoothRemoteGATTCharacteristic.getDescriptor()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که به اولین {{DOMxRef("BluetoothRemoteGATTDescriptor")}} برای یک UUID توصیف‌کننده مشخص حل می‌شود.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.getDescriptors()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که به یک {{JSxRef("Array")}} از تمام اشیاء {{DOMxRef("BluetoothRemoteGATTDescriptor")}} برای یک UUID توصیف‌کننده مشخص حل می‌شود.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.readValue()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که به یک {{JSxRef("DataView")}} حاوی یک کپی از ویژگی `value` در صورت در دسترس بودن و پشتیبانی شدن حل می‌شود. در غیر این صورت یک خطا پرتاب می‌کند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.writeValue()")}} {{Deprecated_Inline}}
  - : ویژگی `value` را به بایت‌های موجود در یک {{JSxRef("ArrayBuffer")}} مشخص تنظیم می‌کند، [مقدار مشخصه را با پاسخ اختیاری می‌نویسد](https://webbluetoothcg.github.io/web-bluetooth/#writecharacteristicvalue) و {{JSxRef("Promise")}} حاصل را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.writeValueWithResponse()")}} {{Experimental_Inline}}
  - : ویژگی `value` را به بایت‌های موجود در یک {{JSxRef("ArrayBuffer")}} مشخص تنظیم می‌کند، [مقدار مشخصه را با پاسخ الزامی می‌نویسد](https://webbluetoothcg.github.io/web-bluetooth/#writecharacteristicvalue) و {{JSxRef("Promise")}} حاصل را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.writeValueWithoutResponse()")}} {{Experimental_Inline}}
  - : ویژگی `value` را به بایت‌های موجود در یک {{JSxRef("ArrayBuffer")}} مشخص تنظیم می‌کند، [مقدار مشخصه را بدون پاسخ می‌نویسد](https://webbluetoothcg.github.io/web-bluetooth/#writecharacteristicvalue) و {{JSxRef("Promise")}} حاصل را برمی‌گرداند.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.startNotifications()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که وقتی `navigator.bluetooth` به زمینه اعلان فعال اضافه می‌شود، حل می‌شود.
- {{DOMxRef("BluetoothRemoteGATTCharacteristic.stopNotifications()")}} {{Experimental_Inline}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که وقتی `navigator.bluetooth` از زمینه اعلان فعال حذف می‌شود، حل می‌شود.

## رویدادها

- {{DOMxRef("BluetoothRemoteGATTCharacteristic/characteristicvaluechanged_event", "characteristicvaluechanged")}} {{Experimental_Inline}}
  - : وقتی مقدار آن تغییر می‌کند، روی یک `BluetoothRemoteGATTCharacteristic` فعال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}