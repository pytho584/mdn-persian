---
title: "AudioWorkletGlobalScope: sampleRate property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletGlobalScope/sampleRate"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletGlobalScope: sampleRate property"
short-title: sampleRate
slug: Web/API/AudioWorkletGlobalScope/sampleRate
page-type: web-api-instance-property
browser-compat: api.AudioWorkletGlobalScope.sampleRate
---

{{APIRef("Web Audio API")}}

ویژگی فقط خواندنی **`sampleRate`** از رابط {{domxref("AudioWorkletGlobalScope")}} یک عدد اعشاری برمی‌گرداند که نرخ نمونه‌برداری {{domxref("BaseAudioContext")}} مرتبطی که وورک‌لت به آن تعلق دارد را نشان می‌دهد.

## مقدار

یک عدد اعشاری که نرخ نمونه‌برداری مرتبط را نشان می‌دهد.

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

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)