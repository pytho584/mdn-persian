---
title: "EncodedAudioChunk: type property"
short-title: type
slug: Web/API/EncodedAudioChunk/type
page-type: web-api-instance-property
browser-compat: api.EncodedAudioChunk.type
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‑خواندنی **`type`** در رابط {{domxref("EncodedAudioChunk")}} مقداری را برمی‌گرداند که نشان می‌دهد آیا تکهٔ صوتی یک تکهٔ کلیدی است که برای رمزگشایی به فریم‌های دیگر وابسته نیست.

## مقدار

یک رشته، یکی از موارد زیر:

- `"key"`
  - : داده یک تکهٔ کلیدی است.
- `"delta"`
  - : داده یک تکهٔ کلیدی نیست.

## مثال‌ها

در مثال زیر، `type` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedAudioChunk(init);

console.log(chunk.type); // "key"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}