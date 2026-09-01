---
title: "EncodedAudioChunk: timestamp property"
short-title: timestamp
slug: Web/API/EncodedAudioChunk/timestamp
page-type: web-api-instance-property
browser-compat: api.EncodedAudioChunk.timestamp
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`timestamp`** از رابط {{domxref("EncodedAudioChunk")}} یک عدد صحیح برمی‌گرداند که نشان‌دهندهٔ زمان‌بندی (timestamp) صوت برحسب میکروثانیه است.

## مقدار

یک عدد صحیح.

## مثال‌ها

در مثال زیر، `timestamp` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: audioBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedAudioChunk(init);

console.log(chunk.timestamp); // 23000000
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}