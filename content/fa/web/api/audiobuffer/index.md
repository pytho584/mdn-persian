---
title: "AudioBuffer"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer"
translated_by: "n8n + AI"
---

---
title: AudioBuffer
slug: Web/API/AudioBuffer
page-type: web-api-interface
browser-compat: api.AudioBuffer
---

{{APIRef("Web Audio API")}}

رابط **`AudioBuffer`** یک قطعه صوتی کوتاه را که در حافظه نگهداری میشود، نشان میدهد و از یک فایل صوتی با استفاده از متد {{ domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()") }} یا از داده خام با استفاده از {{ domxref("BaseAudioContext/createBuffer", "AudioContext.createBuffer()") }} ایجاد میشود. پس از قرار گرفتن در یک AudioBuffer، صدا میتواند با ارسال به یک {{ domxref("AudioBufferSourceNode") }} پخش شود.

اشیاء از این نوع برای نگهداری قطعات صوتی کوچک طراحی شدهاند، معمولاً کمتر از ۴۵ ثانیه. برای صداهای طولانیتر، اشیائی که {{domxref("MediaElementAudioSourceNode")}} را پیادهسازی میکنند مناسبتر هستند. بافر شامل شکل موج سیگنال صوتی است که به صورت یک سری دامنهها در قالب زیر کدگذاری شده است: PCM خطی ۳۲ بیتی IEEE754 غیر درهمآمیخته (non-interleaved) با محدوده اسمی بین `1-` و `1+`، یعنی یک بافر ممیز شناور ۳۲ بیتی، با هر نمونه بین ۱٫۰- و ۱٫۰. اگر `AudioBuffer` دارای چند کانال باشد، آنها در بافرهای جداگانه ذخیره میشوند.

## سازنده

- {{domxref("AudioBuffer.AudioBuffer", "AudioBuffer()")}}
  - : یک نمونه شیء جدید `AudioBuffer` ایجاد و برمیگرداند.

## ویژگیهای نمونه

- {{domxref("AudioBuffer.sampleRate")}} {{ReadOnlyInline}}
  - : یک عدد اعشاری برمیگرداند که نرخ نمونهبرداری، بر حسب نمونه در ثانیه، از داده PCM ذخیرهشده در بافر را نشان میدهد.
- {{domxref("AudioBuffer.length")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمیگرداند که طول، بر حسب فریم نمونه، از داده PCM ذخیرهشده در بافر را نشان میدهد.
- {{domxref("AudioBuffer.duration")}} {{ReadOnlyInline}}
  - : یک عدد double برمیگرداند که مدت زمان، بر حسب ثانیه، از داده PCM ذخیرهشده در بافر را نشان میدهد.
- {{domxref("AudioBuffer.numberOfChannels")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمیگرداند که تعداد کانالهای صوتی مجزا توصیفشده توسط داده PCM ذخیرهشده در بافر را نشان میدهد.

## روشهای نمونه

- {{domxref("AudioBuffer.getChannelData()")}}
  - : یک {{jsxref("Float32Array")}} شامل داده PCM مرتبط با کانال را برمیگرداند که توسط پارامتر `channel` تعریف شده است (با `0` که نشاندهنده اولین کانال است).
- {{domxref("AudioBuffer.copyFromChannel()")}}
  - : نمونهها را از کانال مشخصشده `AudioBuffer` به آرایه `destination` کپی میکند.
- {{domxref("AudioBuffer.copyToChannel()")}}
  - : نمونهها را از آرایه `source` به کانال مشخصشده `AudioBuffer` کپی میکند.

## مثال

مثال ساده زیر نشان میدهد که چگونه یک `AudioBuffer` بسازید و آن را با نویز سفید تصادفی پر کنید. میتوانید کد منبع کامل را در مخزن [webaudio-examples](https://github.com/mdn/webaudio-examples) ما پیدا کنید؛ یک نسخه [اجرای زنده](https://mdn.github.io/webaudio-examples/audio-buffer/) نیز موجود است.

```js
const audioCtx = new AudioContext();

// Create an empty three-second stereo buffer at the sample rate of the AudioContext
const myArrayBuffer = audioCtx.createBuffer(
  2,
  audioCtx.sampleRate * 3,
  audioCtx.sampleRate,
);

// Fill the buffer with white noise;
// just random values between -1.0 and 1.0
for (let channel = 0; channel < myArrayBuffer.numberOfChannels; channel++) {
  // This gives us the actual array that contains the data
  const nowBuffering = myArrayBuffer.getChannelData(channel);
  for (let i = 0; i < myArrayBuffer.length; i++) {
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
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)