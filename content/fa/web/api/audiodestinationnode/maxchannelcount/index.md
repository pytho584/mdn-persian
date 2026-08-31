---
title: "AudioDestinationNode: maxChannelCount property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDestinationNode/maxChannelCount"
translated_by: "n8n + AI"
---

---
title: "AudioDestinationNode: maxChannelCount property"
short-title: maxChannelCount
slug: Web/API/AudioDestinationNode/maxChannelCount
page-type: web-api-instance-property
browser-compat: api.AudioDestinationNode.maxChannelCount
---

{{ APIRef("Web Audio API") }}

ویژگی `maxChannelCount` از رابط {{ domxref("AudioDestinationNode") }} یک `unsigned long` است که حداکثر تعداد کانال‌هایی را که دستگاه فیزیکی می‌تواند مدیریت کند، تعیین می‌کند.

ویژگی {{domxref("AudioNode.channelCount")}} را می‌توان بین ۰ و این مقدار (هر دو شامل) تنظیم کرد. اگر `maxChannelCount` برابر با `۰` باشد، مانند {{domxref("OfflineAudioContext")}}، تعداد کانال قابل تغییر نیست.

## مقدار

یک `unsigned long`.

## مثال‌ها

مثال زیر یک گراف صوتی را راه‌اندازی می‌کند که شامل یک `AudioDestinationNode` با `maxChannelCount` برابر با ۲ است:

```js
const audioCtx = new AudioContext();
const source = audioCtx.createMediaElementSource(myMediaElement);
source.connect(gainNode);
audioCtx.destination.maxChannelCount = 2;
gainNode.connect(audioCtx.destination);
```

برای مشاهده پیاده‌سازی کامل‌تر، یکی از نمونه‌های Web Audio ماز در MDN، مانند [Voice-change-o-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) یا [Violent Theremin](https://mdn.github.io/webaudio-examples/violent-theremin/) را بررسی کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)