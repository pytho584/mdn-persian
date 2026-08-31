---
title: "BluetoothRemoteGATTCharacteristic: writeValueWithResponse() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic/writeValueWithResponse"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTCharacteristic: writeValueWithResponse() method"
short-title: writeValueWithResponse()
slug: Web/API/BluetoothRemoteGATTCharacteristic/writeValueWithResponse
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic.writeValueWithResponse
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTCharacteristic.writeValueWithResponse()`** ویژگی `value` یک شیء {{domxref("BluetoothRemoteGATTCharacteristic")}} را به بایت‌های موجود در یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} داده شده تنظیم می‌کند، [مقدار مشخصه را با پاسخ مورد نیاز می‌نویسد](https://webbluetoothcg.github.io/web-bluetooth/#writecharacteristicvalue) و {{JSxRef("Promise")}} حاصل را بازمی‌گرداند.

## نحو

```js-nolint
writeValueWithResponse(value)
```

### پارامترها

- `value`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}}.

### مقدار بازگشتی

یک {{jsxref("Promise")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}