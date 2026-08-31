---
title: "Blob: arrayBuffer() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/arrayBuffer"
translated_by: "n8n + AI"
---

---
title: "Blob: arrayBuffer() method"
short-title: arrayBuffer()
slug: Web/API/Blob/arrayBuffer
page-type: web-api-instance-method
browser-compat: api.Blob.arrayBuffer
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`arrayBuffer()`** از رابط {{domxref("Blob")}} یک {{jsxref("Promise")}} برمی‌گرداند که با محتویات blob به‌صورت دادهٔ باینری موجود در یک {{jsxref("ArrayBuffer")}} حل می‌شود.

## سینتکس

```js-nolint
arrayBuffer()
```

### پارامترها

هیچ.

### مقدار بازگشتی

پرامیزی که با یک {{jsxref("ArrayBuffer")}} حاوی داده‌های blob به شکل باینری حل می‌شود.

### استثناها

اگرچه این متد استثنا پرتاب نمی‌کند، ممکن است پرامیس را رد کند. این ممکن است برای مثال زمانی رخ دهد که خواننده‌ای که برای دریافت داده‌های blob استفاده می‌شود، استثنا پرتاب کند. هر استثنایی که هنگام دریافت داده‌ها پرتاب شود، به رد شدن (rejection) تبدیل می‌شود.

## یادداشت‌های استفاده

اگرچه این متد شبیه متد {{domxref("FileReader.readAsArrayBuffer()")}} است، اما `arrayBuffer()` به‌جای اینکه یک API مبتنی بر رویداد باشد (مانند متد رابط `FileReader`)، یک promise برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Response.arrayBuffer()")}}
- [Streams API](/en-US/docs/Web/API/Streams_API)
- {{domxref("FileReader.readAsArrayBuffer()")}}