---
title: "BaseAudioContext: createBufferSource() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createBufferSource"
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

متد `createBufferSource()` از رابط {{ domxref("BaseAudioContext") }} برای ایجاد یک {{ domxref("AudioBufferSourceNode") }} جدید استفاده می‌شود که می‌تواند برای پخش داده‌های صوتی موجود در یک شیء {{ domxref("AudioBuffer") }} به کار رود. اشیاء {{domxref("AudioBuffer")}} با استفاده از {{domxref("BaseAudioContext.createBuffer")}} ایجاد می‌شوند یا توسط {{domxref("BaseAudioContext.decodeAudioData")}} زمانی که یک آهنگ صوتی را با موفقیت رمزگشایی کند، بازگردانده می‌شوند.

> [!NOTE]
> سازنده {{domxref("AudioBufferSourceNode.AudioBufferSourceNode", "AudioBufferSourceNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("AudioBufferSourceNode")}} است؛ برای اطلاعات بیشتر به
> [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## Syntax

```js-nolint
createBufferSource()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("AudioBufferSourceNode")}}.

## مثال‌ها

در این مثال، یک بافر دو ثانیه‌ای ایجاد می‌کنیم، آن را با نویز سفید پر می‌کنیم و سپس آن را از طریق یک {{ domxref("AudioBufferSourceNode") }} پخش می‌کنیم. توضیحات درون کد به روشنی روند کار را نشان می‌دهند.

> [!NOTE]
> همچنین می‌توانید [کد را به صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer/)،
> یا [متن منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/blob/main/audio-buffer/index.html).

```js
const audioCtx = new AudioContext();
const button = document.querySelector("button");
const pre = document.querySelector("pre");
const myScript = document.querySelector("script");

pre.textContent = myScript.textContent;

// Stereo
const channels = 2;
// Create an empty two second stereo buffer at the
// sample rate of the AudioContext
const frameCount = audioCtx.sampleRate * 2.0;

const myArrayBuffer = audioCtx.createBuffer(
  channels,
  frameCount,
  audioCtx.sampleRate,
);

button.onclick = () => {
  // Fill the buffer with white noise;
  // just random values between -1.0 and 1.0
  for (let channel = 0; channel < channels; channel++) {
    // This gives us the actual ArrayBuffer that contains the data
    const nowBuffering = myArrayBuffer.getChannelData(channel);
    for (let i = 0; i < frameCount; i++) {
      // Math.random() is in [0; 1.0]
      // audio needs to be in [-1.0; 1.0]
      nowBuffering[i] = Math.random() * 2 - 1;
    }
  }

  // Get an AudioBufferSourceNode.
  // This is the AudioNode to use when we want to play an AudioBuffer
  const source = audioCtx.createBufferSource();
  // set the buffer in the AudioBufferSourceNode
  source.buffer = myArrayBuffer;
  // connect the AudioBufferSourceNode to the
  // destination so we can hear the sound
  source.connect(audioCtx.destination);
  // start the source playing
  source.start();
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)