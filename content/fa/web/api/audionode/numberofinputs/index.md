---
title: "AudioNode: numberOfInputs property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/numberOfInputs"
translated_by: "n8n + AI"
short-title: numberOfInputs
slug: Web/API/AudioNode/numberOfInputs
page-type: web-api-instance-property
browser-compat: api.AudioNode.numberOfInputs
---

{{APIRef("Web Audio API")}}

ویژگی `numberOfInputs` از رابط {{domxref("AudioNode")}} تعداد ورودی‌هایی که به گره تغذیه می‌شوند را برمی‌گرداند. گره‌های منبع به عنوان گره‌هایی تعریف می‌شوند که ویژگی `numberOfInputs` آن‌ها مقدار 0 دارد.

## مقدار

یک عدد صحیح ≥ 0.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode).connect(audioCtx.destination);

console.log(oscillator.numberOfInputs); // 0
console.log(gainNode.numberOfInputs); // 1
console.log(audioCtx.destination.numberOfInputs); // 1
```

## مشخصات فنی

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)