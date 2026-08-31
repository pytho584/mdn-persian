---
title: "AudioBuffer: numberOfChannels property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/numberOfChannels"
translated_by: "n8n + AI"
short-title: numberOfChannels
slug: Web/API/AudioBuffer/numberOfChannels
page-type: web-api-instance-property
browser-compat: api.AudioBuffer.numberOfChannels
---

{{ APIRef("Web Audio API") }}

ویژگی `numberOfChannels` از رابط {{ domxref("AudioBuffer") }} یک عدد صحیح را برمی‌گرداند که نشان‌دهنده تعداد کانال‌های مجزای صوتی توصیف‌شده توسط داده‌های PCM ذخیره‌شده در بافر است.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
// Stereo
const channels = 2;

// یک بافر استریوی دو ثانیه‌ای خالی با نرخ نمونه‌برداری AudioContext ایجاد کنید
const frameCount = audioCtx.sampleRate * 2.0;
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);

button.onclick = () => {
  // بافر را با نویز سفید پر کنید؛
  // فقط مقادیر تصادفی بین 1.0- و 1.0
  for (let channel = 0; channel < channels; channel++) {
    // این به ما ArrayBuffer واقعی حاوی داده‌ها را می‌دهد
    const nowBuffering = myArrayBuffer.getChannelData(channel);
    for (let i = 0; i < frameCount; i++) {
      // Math.random() در بازه [0; 1.0] است
      // صدا باید در بازه [1.0-; 1.0] باشد
      nowBuffering[i] = Math.random() * 2 - 1;
    }
  }

  console.log(myArrayBuffer.numberOfChannels);
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)