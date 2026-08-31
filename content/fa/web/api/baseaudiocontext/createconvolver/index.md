---
title: "BaseAudioContext: createConvolver() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createConvolver"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createConvolver() method"
short-title: createConvolver()
slug: Web/API/BaseAudioContext/createConvolver
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createConvolver
---

{{ APIRef("Web Audio API") }}

متد `createConvolver()` از رابط {{ domxref("BaseAudioContext") }} یک {{ domxref("ConvolverNode") }} ایجاد می‌کند که معمولاً برای اعمال افکت‌های ریورب به صدای شما استفاده می‌شود. برای اطلاعات بیشتر به [تعریف مشخصات Convolution](https://webaudio.github.io/web-audio-api/#background-3) مراجعه کنید.

> [!NOTE]
> سازنده {{domxref("ConvolverNode.ConvolverNode", "ConvolverNode()")}}
> روش توصیه‌شده برای ایجاد یک {{domxref("ConvolverNode")}} است؛ به
> [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## نحو

```js-nolint
createConvolver()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{domxref("ConvolverNode")}}.

## مثال‌ها

### ایجاد یک گره کانولور

مثال زیر نحوه استفاده از یک AudioContext برای ایجاد یک گره کانولور را نشان می‌دهد.
شما یک {{domxref("AudioBuffer")}} حاوی یک نمونه صوتی ایجاد می‌کنید که به عنوان
محیط برای شکل‌دهی به کانولوشن (به نام _پاسخ ضربه_) استفاده می‌شود و
آن را روی کانولور اعمال می‌کنید. مثال زیر از یک نمونه کوتاه از جمعیت سالن کنسرت
استفاده می‌کند، بنابراین افکت ریورب اعمال‌شده واقعاً عمیق و پرطنین است.

برای مثال‌های کاربردی کامل‌تر/اطلاعات بیشتر، دموی [Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) ما را ببینید (برای کدی که در زیر گزیده شده است، [app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js) را ببینید).

```js
const audioCtx = new AudioContext();
// …

const convolver = audioCtx.createConvolver();
// …

// Grab audio track via fetch() for convolver node
try {
  const response = await fetch(
    "https://mdn.github.io/voice-change-o-matic/audio/concert-crowd.ogg",
  );
  const arrayBuffer = await response.arrayBuffer();
  const decodedAudio = await audioCtx.decodeAudioData(arrayBuffer);
  convolver.buffer = decodedAudio;
} catch (error) {
  console.error(
    `Unable to fetch the audio file: ${name} Error: ${err.message}`,
  );
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)