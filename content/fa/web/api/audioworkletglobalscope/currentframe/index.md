---
title: "AudioWorkletGlobalScope: currentFrame property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletGlobalScope/currentFrame"
translated_by: "n8n + AI"
---
---
title: "AudioWorkletGlobalScope: currentFrame property"
short-title: currentFrame
slug: Web/API/AudioWorkletGlobalScope/currentFrame
page-type: web-api-instance-property
browser-compat: api.AudioWorkletGlobalScope.currentFrame
---

{{APIRef("Web Audio API")}}

ویژگی فقط خواندنی **`currentFrame`** از رابط {{domxref("AudioWorkletGlobalScope")}} یک عدد صحیح را برمی‌گرداند که نشان‌دهنده فریم نمونه فعلی و همیشه در حال افزایش بلوک صوتی در حال پردازش است. این مقدار پس از پردازش هر بلوک صوتی به اندازه ۱۲۸ (اندازه یک کوانتوم رندر) افزایش می‌یابد.

## مقدار

یک عدد صحیح.

## مثال‌ها

{{domxref("AudioWorkletProcessor")}} به ویژگی‌های خاص {{domxref("AudioWorkletGlobalScope")}} دسترسی دارد:

```js
// AudioWorkletProcessor defined in : test-processor.js
class TestProcessor extends AudioWorkletProcessor {
  constructor() {
    super();

    // Logs the current sample-frame and time at the moment of instantiation.
    // They are accessible from the AudioWorkletGlobalScope.
    console.log(currentFrame);
    console.log(currentTime);
  }

  // The process method is required - output silence,
  // which the outputs are already filled with.
  process(inputs, outputs, parameters) {
    return true;
  }
}

// Logs the sample rate, that is not going to change ever,
// because it's a read-only property of a BaseAudioContext
// and is set only during its instantiation.
console.log(sampleRate);

// You can declare any variables and use them in your processors
// for example it may be an ArrayBuffer with a wavetable.
const usefulVariable = 42;
console.log(usefulVariable);

registerProcessor("test-processor", TestProcessor);
```

اسکریپت اصلی پردازنده را بارگذاری می‌کند، یک نمونه از {{domxref("AudioWorkletNode")}} ایجاد می‌کند، نام پردازنده را به آن می‌دهد، و گره را به یک گراف صوتی متصل می‌کند. ما باید خروجی فراخوانی‌های {{domxref("console/log_static", "console.log()")}} را در کنسول ببینیم:

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("test-processor.js");
const testNode = new AudioWorkletNode(audioContext, "test-processor");
testNode.connect(audioContext.destination);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API وب صوتی](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از API وب صوتی](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)