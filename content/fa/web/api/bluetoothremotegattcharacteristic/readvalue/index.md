---
title: "BluetoothRemoteGATTCharacteristic: readValue() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTCharacteristic/readValue"
translated_by: "n8n + AI"
---

---
title: "BluetoothRemoteGATTCharacteristic: readValue() method"
short-title: readValue()
slug: Web/API/BluetoothRemoteGATTCharacteristic/readValue
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.BluetoothRemoteGATTCharacteristic.readValue
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`BluetoothRemoteGATTCharacteristic.readValue()`** یک {{jsxref("Promise")}} برمی‌گرداند که به یک {{jsxref("DataView")}} شامل نسخه‌ای از ویژگی `value` (در صورت موجود بودن و پشتیبانی شدن) تبدیل می‌شود. در غیر این صورت، یک خطا پرتاب می‌کند.

### نحو

```js-nolint
readValue()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک {{jsxref("DataView")}} تبدیل می‌شود.

### مشخصات

{{Specifications}}

### سازگاری مرورگر

{{Compat}}