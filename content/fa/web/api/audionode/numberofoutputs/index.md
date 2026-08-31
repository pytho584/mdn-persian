---
title: "AudioNode: numberOfOutputs property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/numberOfOutputs"
translated_by: "n8n + AI"
---

---
title: "AudioNode: numberOfOutputs property"
short-title: numberOfOutputs
slug: Web/API/AudioNode/numberOfOutputs
page-type: web-api-instance-property
browser-compat: api.AudioNode.numberOfOutputs
---

{{APIRef("Web Audio API")}}

ویژگی `numberOfOutputs` از رابط {{ domxref("AudioNode") }} تعداد خروجی‌های خارج‌شده از گره را برمی‌گرداند. گره‌های مقصد — مانند {{domxref("AudioDestinationNode") }} — برای این ویژگی مقدار ۰ دارند.

## مقدار

یک عدد صحیح ≥ ۰.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode).connect(audioCtx.destination);

console.log(oscillator.numberOfOutputs); // 1
console.log(gainNode.numberOfOutputs); // 1
console.log(audioCtx.destination.numberOfOutputs); // 0
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)