---
title: "BluetoothRemoteGATTCharacteristic: writeValueWithoutResponse() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic/writeValueWithoutResponse"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTCharacteristic: writeValueWithoutResponse() method"
short-title: writeValueWithoutResponse()
slug: Web/API/BluetoothRemoteGATTCharacteristic/writeValueWithoutResponse
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic.writeValueWithoutResponse
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTCharacteristic.writeValueWithoutResponse()`** ویژگی `value` یک شیء {{domxref("BluetoothRemoteGATTCharacteristic")}} را به بایت‌های موجود در یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} تنظیم می‌کند، [مقدار مشخصه را بدون پاسخ می‌نویسد](https://webbluetoothcg.github.io/web-bluetooth/#writecharacteristicvalue)، و {{JSxRef("Promise")}} حاصل را برمی‌گرداند.

## Syntax

```js-nolint
writeValueWithoutResponse(value)
```

### Parameters

- `value`
  - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}}.

### Return value

یک {{jsxref("Promise")}}.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}