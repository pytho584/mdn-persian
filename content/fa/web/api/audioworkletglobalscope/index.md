---
title: "AudioWorkletGlobalScope"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletGlobalScope"
translated_by: "n8n + AI"
---

---
title: AudioWorkletGlobalScope
slug: Web/API/AudioWorkletGlobalScope
page-type: web-api-interface
browser-compat: api.AudioWorkletGlobalScope
---

{{APIRef("Web Audio API")}}

واسط **`AudioWorkletGlobalScope`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک زمینه اجرای سراسری برای کد ارائه‌شده توسط کاربر را نشان می‌دهد که کلاس‌های سفارشی مشتق‌شده از {{domxref("AudioWorkletProcessor")}} را تعریف می‌کند.

هر {{domxref("BaseAudioContext")}} یک {{domxref("AudioWorklet")}} واحد دارد که تحت ویژگی {{domxref("BaseAudioContext.audioWorklet", "audioWorklet")}} در دسترس است و کد خود را در یک `AudioWorkletGlobalScope` واحد اجرا می‌کند.

از آنجایی که زمینه اجرای سراسری در سراسر `BaseAudioContext` جاری به اشتراک گذاشته می‌شود، می‌توان هر متغیر دیگری را تعریف کرد و هر عملی را که در worklet‌ها مجاز است انجام داد - به جز تعریف کلاس‌های مشتق‌شده از `AudioWorkletProcessor`.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این واسط همچنین ویژگی‌های تعریف‌شده در واسط والد خود، {{domxref("WorkletGlobalScope")}} را به ارث می‌برد._

- {{domxref("AudioWorkletGlobalScope.currentFrame", "currentFrame")}} {{ReadOnlyInline}}
  - : یک عدد صحیح را برمی‌گرداند که نشان‌دهنده فریم نمونه فعلی و در حال افزایش بلوک صوتی در حال پردازش است. پس از پردازش هر بلوک صوتی ۱۲۸ (اندازه یک کوانتوم رندر) افزایش می‌یابد.
- {{domxref("AudioWorkletGlobalScope.currentTime", "currentTime")}} {{ReadOnlyInline}}
  - : یک عدد اعشاری را برمی‌گرداند که نشان‌دهنده زمان زمینه در حال افزایش بلوک صوتی در حال پردازش است. این مقدار برابر با ویژگی {{domxref("BaseAudioContext.currentTime", "currentTime")}} مربوط به {{domxref("BaseAudioContext")}}ای است که worklet به آن تعلق دارد.
- {{domxref("AudioWorkletGlobalScope.sampleRate", "sampleRate")}} {{ReadOnlyInline}}
  - : یک عدد اعشاری را برمی‌گرداند که نشان‌دهنده نرخ نمونه مربوط به {{domxref("BaseAudioContext")}} است.
- {{domxref("AudioWorkletGlobalScope.port", "port")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک {{domxref("MessagePort")}} برای ارتباط ناهمزمان سفارشی بین کد در رشته اصلی و دامنه سراسری یک audio worklet برمی‌گرداند. این امکان ارسال و دریافت پیام‌های سفارشی مانند داده‌های کنترل یا تنظیمات سراسری را فراهم می‌کند.

## روش‌های نمونه

_این واسط همچنین روش‌های تعریف‌شده در واسط والد خود، {{domxref("WorkletGlobalScope")}} را به ارث می‌برد._

- {{domxref("AudioWorkletGlobalScope.registerProcessor", "registerProcessor()")}}
  - : یک کلاس مشتق‌شده از واسط {{domxref('AudioWorkletProcessor')}} را ثبت می‌کند. سپس می‌توان از این کلاس با ایجاد یک {{domxref("AudioWorkletNode")}} با استفاده از نام ثبت‌شده آن استفاده کرد.

## مثال‌ها

در این مثال، تمام ویژگی‌های سراسری را در سازنده یک {{domxref("AudioWorkletProcessor")}} سفارشی در کنسول چاپ می‌کنیم.

ابتدا باید پردازنده را تعریف کرده و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

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
// for example it may be an ArrayBuffer with a wavetable
const usefulVariable = 42;
console.log(usefulVariable);

registerProcessor("test-processor", TestProcessor);
```

سپس، در فایل اسکریپت اصلی خود، پردازنده را بارگذاری می‌کنیم، یک نمونه از {{domxref("AudioWorkletNode")}} - با نام پردازنده - ایجاد می‌کنیم و آن را به یک گراف صوتی متصل می‌کنیم. باید خروجی فراخوانی‌های {{domxref("console/log_static", "console.log()")}} را در کنسول ببینیم:

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
- [استفاده از AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)