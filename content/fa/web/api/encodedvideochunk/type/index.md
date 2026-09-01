---
title: "EncodedVideoChunk: type property"
short-title: type
slug: Web/API/EncodedVideoChunk/type
page-type: web-api-instance-property
browser-compat: api.EncodedVideoChunk.type
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

خاصیت فقط‌خواندنی **`type`** از رابط {{domxref("EncodedVideoChunk")}} مقداری را برمی‌گرداند که نشان می‌دهد آیا تکه ویدیو یک تکه کلیدی است که برای رمزگشایی به فریم‌های دیگر وابسته نیست.

## مقدار

یک رشته، یکی از موارد زیر:

- `"key"`
  - : داده یک تکه کلیدی است.
- `"delta"`
  - : داده یک تکه کلیدی نیست.

## مثال‌ها

در مثال زیر، `type` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedVideoChunk(init);

console.log(chunk.type); // "key"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}