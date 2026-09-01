---
title: "EncodedVideoChunk: byteLength property"
short-title: byteLength
slug: Web/API/EncodedVideoChunk/byteLength
page-type: web-api-instance-property
browser-compat: api.EncodedVideoChunk.byteLength
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`byteLength`** از رابط {{domxref("EncodedVideoChunk")}} طول داده‌های ویدیویی کدگذاری‌شده را بر حسب بایت برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، `byteLength` در کنسول چاپ شده است.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedVideoChunk(init);

console.log(chunk.byteLength); // 352800
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}