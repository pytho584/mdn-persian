---
title: "AudioWorkletNode: parameters property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletNode/parameters"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletNode: parameters property"
short-title: parameters
slug: Web/API/AudioWorkletNode/parameters
page-type: web-api-instance-property
browser-compat: api.AudioWorkletNode.parameters
---

{{APIRef("Web Audio API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`parameters`** از رابط {{domxref("AudioWorkletNode")}}، {{domxref("AudioParamMap")}} مرتبط را بازمی‌گرداند — یعنی مجموعه‌ای شبیه به `Map` از اشیاء {{domxref("AudioParam")}}. این اشیاء در زمان ایجاد {{domxref("AudioWorkletProcessor")}} زیرین، بر اساس دریافت‌کنندهٔ ایستای {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} آن نمونه‌سازی می‌شوند.

## مقدار

شیء {{domxref("AudioParamMap")}} شامل نمونه‌های {{domxref("AudioParam")}}. این‌ها را می‌توان به همان روشی که با گره‌های `AudioNode` پیش‌فرض خودکار می‌شوند، خودکار کرد و مقادیر محاسبه‌شدهٔ آن‌ها را می‌توان در متد {{domxref("AudioWorkletProcessor.process", "process")}} مربوط به {{domxref("AudioWorkletProcessor")}} استفاده کرد.

## مثال‌ها

برای نشان دادن ایجاد و استفاده از `AudioParam`های سفارشی، مثال صفحهٔ {{domxref("AudioWorkletNode")}} را گسترش می‌دهیم. در آنجا یک گرهٔ ساده ساختیم که نویز سفید خروجی می‌دهد. در اینجا، به‌علاوه، یک پارامتر بهرهٔ سفارشی ایجاد می‌کنیم تا بتوانیم مستقیماً بلندی صدای خروجی را تغییر دهیم (اگرچه برای این منظور می‌توانید از {{domxref("GainNode")}} نیز استفاده کنید).

ابتدا باید یک `AudioWorkletProcessor` سفارشی تعریف کرده و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

ما پردازنده را با افزودن یک دریافت‌کنندهٔ ایستای {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} گسترش می‌دهیم. این دریافت‌کننده به‌صورت داخلی توسط سازندهٔ `AudioWorkletNode` برای پر کردن `parameters` آن با اشیاء `AudioParam` نمونه‌سازی‌شده استفاده خواهد شد.

```js
// white-noise-processor.js
class WhiteNoiseProcessor extends AudioWorkletProcessor {
  static get parameterDescriptors() {
    return [
      {
        name: "customGain",
        defaultValue: 1,
        minValue: 0,
        maxValue: 1,
        automationRate: "a-rate",
      },
    ];
  }

  process(inputs, outputs, parameters) {
    const output = outputs[0];
    output.forEach((channel) => {
      for (let i = 0; i < channel.length; i++) {
        channel[i] =
          (Math.random() * 2 - 1) *
          (parameters["customGain"].length > 1
            ? parameters["customGain"][i]
            : parameters["customGain"][0]);
        // note: a parameter contains an array of 128 values (one value for each of 128 samples),
        // however it may contain a single value which is to be used for all 128 samples
        // if no automation is scheduled for the moment.
      }
    });
    return true;
  }
}

registerProcessor("white-noise-processor", WhiteNoiseProcessor);
```

سپس، در فایل اصلی اسکریپت، پردازنده را بارگذاری می‌کنیم، نمونه‌ای از `AudioWorkletNode` با ارسال نام پردازنده می‌سازیم و گره را به گراف صوتی متصل می‌کنیم.

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("white-noise-processor.js");
const whiteNoiseNode = new AudioWorkletNode(
  audioContext,
  "white-noise-processor",
);
whiteNoiseNode.connect(audioContext.destination);
```

اکنون می‌توانیم بهره را روی گره به این صورت تغییر دهیم:

```js
const gainParam = whiteNoiseNode.parameters.get("customGain");
gainParam.setValueAtTime(0, audioContext.currentTime);
gainParam.linearRampToValueAtTime(0.5, audioContext.currentTime + 0.5);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)