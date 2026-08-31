---
title: "BluetoothRemoteGATTDescriptor: readValue() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTDescriptor/readValue"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTDescriptor: readValue() method"
short-title: readValue()
slug: Web/API/BluetoothRemoteGATTDescriptor/readValue
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTDescriptor.readValue
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTDescriptor.readValue()`** یک {{jsxref("Promise")}} برمی‌گرداند که اگر خاصیت `value` موجود و پشتیبانی شود، به یک {{jsxref("DataView")}} شامل یک کپی از آن حل می‌شود؛ در غیر این صورت خطا پرتاب می‌کند.

## نحو

```js-nolint
readValue()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک {{jsxref("DataView")}} حل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}