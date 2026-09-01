---
title: "EncodedAudioChunk: byteLength property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/EncodedAudioChunk/byteLength"
---

---
title: "EncodedAudioChunk: byteLength property"
short-title: byteLength
slug: Web/API/EncodedAudioChunk/byteLength
page-type: web-api-instance-property
browser-compat: api.EncodedAudioChunk.byteLength
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`byteLength`** در رابط {{domxref("EncodedAudioChunk")}} طول داده‌های صوتی کدشده را بر حسب بایت برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، مقدار `byteLength` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedAudioChunk(init);

console.log(chunk.byteLength); // 352800
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}