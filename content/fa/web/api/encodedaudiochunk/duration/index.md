---
title: "EncodedAudioChunk: duration property"
---
---
title: "EncodedAudioChunk: duration property"
short-title: duration
slug: Web/API/EncodedAudioChunk/duration
page-type: web-api-instance-property
browser-compat: api.EncodedAudioChunk.duration
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`duration`** در رابط {{domxref("EncodedAudioChunk")}} یک عدد صحیح برمی‌گرداند که مدت‌زمان صدا را به میکروثانیه نشان می‌دهد.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، `duration` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedAudioChunk(init);

console.log(chunk.duration); // 2000000
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}