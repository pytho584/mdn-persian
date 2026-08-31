---
title: "AudioBuffer: getChannelData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/getChannelData"
translated_by: "n8n + AI"
---

---
title: "AudioBuffer: getChannelData() method"
short-title: getChannelData()
slug: Web/API/AudioBuffer/getChannelData
page-type: web-api-instance-method
browser-compat: api.AudioBuffer.getChannelData
---

{{ APIRef("Web Audio API") }}

متد **`getChannelData()`** از رابط {{ domxref("AudioBuffer") }} یک {{jsxref("Float32Array")}} شامل داده‌های PCM مرتبط با کانال را برمی‌گرداند، که با پارامتر `channel` تعریف می‌شود (با ۰ که نشان‌دهندهٔ اولین کانال است).

## نحو

```js-nolint
getChannelData(channel)
```

### پارامترها

- `channel`
  - : ویژگی `channel` یک اندیس است که کانال خاصی را برای دریافت داده نمایش می‌دهد. مقدار اندیس ۰ نشان‌دهندهٔ اولین کانال است. اگر مقدار اندیس `channel` بزرگ‌تر یا مساوی با {{domxref("AudioBuffer.numberOfChannels")}} باشد، یک استثنای `INDEX_SIZE_ERR` پرتاب می‌شود.

### مقدار بازگشتی

یک {{jsxref("Float32Array")}}.

## مثال‌ها

در مثال زیر، یک بافر دو ثانیه‌ای ایجاد می‌کنیم، آن را با نویز سفید پر می‌کنیم و سپس از طریق یک {{ domxref("AudioBufferSourceNode") }} پخش می‌کنیم. کامنت‌ها باید به‌وضوح توضیح دهند که چه اتفاقی می‌افتد. همچنین می‌توانید [اجرای زندهٔ کد](https://mdn.github.io/webaudio-examples/audio-buffer/) را ببینید یا [مشاهدهٔ منبع](https://github.com/mdn/webaudio-examples).

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

const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)