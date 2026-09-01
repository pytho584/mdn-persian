---
title: "EncodedVideoChunk: timestamp property"
short-title: timestamp
slug: Web/API/EncodedVideoChunk/timestamp
page-type: web-api-instance-property
browser-compat: api.EncodedVideoChunk.timestamp
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`timestamp`** از رابط {{domxref("EncodedVideoChunk")}} یک عدد صحیح را برمی‌گرداند که نشان‌دهندهٔ برچسب زمانی ویدیو بر حسب میکروثانیه است.

## مقدار

یک عدد صحیح.

## نمونه‌ها

در نمونهٔ زیر، `timestamp` در کنسول چاپ می‌شود.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedVideoChunk(init);
console.log(chunk.timestamp); // 23000000
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}