---
title: "BluetoothRemoteGATTDescriptor: writeValue() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTDescriptor/writeValue"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTDescriptor: writeValue() method"
short-title: writeValue()
slug: Web/API/BluetoothRemoteGATTDescriptor/writeValue
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTDescriptor.writeValue
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTDescriptor.writeValue()`** ویژگی مقدار (value) را به بایت‌های موجود در یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} تنظیم می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
writeValue(buffer)
```

### پارامترها

- `buffer`
  - : مقدار را با بایت‌های موجود در بافر تنظیم می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}}.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}