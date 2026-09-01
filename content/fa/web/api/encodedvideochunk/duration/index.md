```
---
title: "EncodedVideoChunk: duration property"
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی **`duration`** (فقطخواندنی) از رابط {{domxref("EncodedVideoChunk")}} یک عدد صحیح برمیگرداند که مدتزمان ویدیو را بر حسب میکروثانیه نشان میدهد.

## مقدار

یک عدد صحیح.

## مثالها

در مثال زیر، مقدار `duration` در کنسول چاپ میشود.

```js
const init = {
  type: "key",
  data: videoBuffer,
  timestamp: 23000000,
  duration: 2000000,
};
const chunk = new EncodedVideoChunk(init);

console.log(chunk.duration); // 2000000
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```