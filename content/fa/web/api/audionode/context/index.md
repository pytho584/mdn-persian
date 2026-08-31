---
title: "AudioNode: context property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/context"
translated_by: "n8n + AI"
---

---
title: "AudioNode: context property"
short-title: context
slug: Web/API/AudioNode/context
page-type: web-api-instance-property
browser-compat: api.AudioNode.context
---

{{APIRef("Web Audio API")}}

خاصیت `context` فقط‌خواندنی در رابط {{domxref("AudioNode")}}، شیء مرتبط با {{domxref("BaseAudioContext")}} را برمی‌گرداند؛ یعنی همان شیئی که نمودار پردازشی را که گره در آن مشارکت دارد نشان می‌دهد.

## مقدار

شیء {{domxref("AudioContext")}} یا {{domxref("OfflineAudioContext")}} که برای ساخت این `AudioNode` استفاده شده است.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();
oscillator.connect(gainNode).connect(audioCtx.destination);

console.log(oscillator.context); // AudioContext
console.log(oscillator.context === audioCtx); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)