---
title: "AudioNode: channelCount property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/channelCount"
translated_by: "n8n + AI"
---

---
title: "AudioNode: channelCount property"
short-title: channelCount
slug: Web/API/AudioNode/channelCount
page-type: web-api-instance-property
browser-compat: api.AudioNode.channelCount
---

{{ APIRef("Web Audio API") }}

ویژگی **`channelCount`** در رابط {{ domxref("AudioNode") }} یک عدد صحیح است که برای تعیین تعداد کانال‌هایی که هنگام [up-mixing and down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصال‌ها به هر ورودی گره استفاده می‌شود، به کار می‌رود.

استفاده و تعریف دقیق `channelCount` به مقدار {{domxref("AudioNode.channelCountMode")}} بستگی دارد:

- اگر مقدار `channelCountMode` برابر با `max` باشد، نادیده گرفته می‌شود.
- اگر مقدار `channelCountMode` برابر با `clamped-max` باشد، به عنوان یک مقدار حداکثر استفاده می‌شود.
- اگر مقدار `channelCountMode` برابر با `explicit` باشد، به عنوان مقدار دقیق استفاده می‌شود.

## مقدار

یک عدد صحیح.

## مثال

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioCtx.destination);

oscillator.channelCount;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)