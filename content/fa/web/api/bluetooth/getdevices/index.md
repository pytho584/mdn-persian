---
title: "Bluetooth: getDevices() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth/getDevices"
translated_by: "n8n + AI"
---

---
title: "Bluetooth: getDevices() method"
short-title: getDevices()
slug: Web/API/Bluetooth/getDevices
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Bluetooth.getDevices
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`getDevices()`** از رابط {{DOMxRef("Bluetooth")}} آرایه‌ای از دستگاه‌های بلوتوث را برمی‌گرداند که این مبدأ اجازه دسترسی به آن‌ها را دارد — از جمله دستگاه‌هایی که خارج از محدوده هستند یا خاموش می‌باشند.

## سینتکس

```js-nolint
getDevices()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{JSxRef("Promise")}} که با آرایه‌ای از اشیاء {{DOMxRef("BluetoothDevice")}} حل می‌شود.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که این عملیات در این زمینه به دلیل [نگرانی‌های امنیتی](/en-US/docs/Web/API/Web_Bluetooth_API#security_considerations) مجاز نباشد؛ مانند زمانی که متد در حالی فراخوانی می‌شود که دسترسی به سند جاری توسط دستور [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) {{HTTPHeader("Permissions-Policy/bluetooth","bluetooth")}} مسدود شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}