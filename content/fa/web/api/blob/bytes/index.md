---
title: "Blob: bytes() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/bytes"
translated_by: "n8n + AI"
---

---
title: "Blob: bytes() method"
short-title: bytes()
slug: Web/API/Blob/bytes
page-type: web-api-instance-method
browser-compat: api.Blob.bytes
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`bytes()`** از رابط {{domxref("Blob")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{jsxref("Uint8Array")}} حاوی محتویات blob به عنوان آرایه‌ای از بایت‌ها resolve می‌شود.

## نحو

```js-nolint
bytes()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شی {{jsxref("Uint8Array")}} حاوی داده‌های blob fulfilled می‌شود.

### استثناها

این متد {{jsxref("Promise")}} بازگشتی را reject می‌کند اگر مثلاً خواننده‌ای که برای واکشی داده‌های blob استفاده می‌شود یک استثنا پرتاب کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}