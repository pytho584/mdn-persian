---
title: "AudioWorkletProcessor: AudioWorkletProcessor() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletProcessor/AudioWorkletProcessor"
translated_by: "n8n + AI"
---

{{APIRef("Web Audio API")}}

سازنده **`AudioWorkletProcessor()`** یک شیء جدید {{domxref("AudioWorkletProcessor")}} ایجاد می‌کند که نشان‌دهنده یک مکانیزم پردازش صوتی زیربنایی از یک {{domxref("AudioWorkletNode")}} است.

> [!NOTE]
> کلاس `AudioWorkletProcessor` و کلاس‌هایی که از آن مشتق می‌شوند نمی‌توانند مستقیماً از کد ارائه‌شده توسط کاربر نمونه‌سازی شوند. در عوض، آنها فقط به صورت داخلی با ایجاد یک {{domxref("AudioWorkletNode")}} مرتبط ساخته می‌شوند.

## Syntax

```js-nolint
new AudioWorkletProcessor(options)
```

### Parameters

- `options`
  - : یک شیء که به عنوان پارامتر _options_ به سازنده {{domxref("AudioWorkletNode.AudioWorkletNode", "AudioWorkletNode()")}} ارسال می‌شود و از طریق [الگوریتم کلون ساختاریافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) عبور می‌کند. ویژگی‌های موجود به شرح زیر است:

    <!-- The specification refers to this object as: AudioWorkletNodeOptions -->
    - `numberOfInputs` {{optional_inline}}
      - : مقداری که برای مقداردهی اولیه ویژگی {{domxref("AudioNode.numberOfInputs", "numberOfInputs")}} استفاده می‌شود. پیش‌فرض ۱ است.
    - `numberOfOutputs` {{optional_inline}}
      - : مقداری که برای مقداردهی اولیه ویژگی {{domxref("AudioNode.numberOfOutputs", "numberOfOutputs")}} استفاده می‌شود. پیش‌فرض ۱ است.
    - `outputChannelCount` {{optional_inline}}
      - : یک **آرایه** که تعداد کانال‌های هر خروجی را تعریف می‌کند. به عنوان مثال، _outputChannelCount: [n, m]_ تعداد کانال‌ها در خروجی اول را _n_ و خروجی دوم را _m_ مشخص می‌کند. طول آرایه باید با `numberOfOutputs` مطابقت داشته باشد.
    - `parameterData` {{optional_inline}}
      - : یک شیء حاوی مقادیر اولیه اشیاء {{domxref("AudioParam")}} سفارشی روی این گره (در ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} آن)، که `key` نام پارامتر سفارشی و `value` مقدار اولیه آن است.
    - `processorOptions` {{optional_inline}}
      - : هر داده اضافی که می‌تواند برای مقداردهی اولیه سفارشی {{domxref("AudioWorkletProcessor")}} زیربنایی استفاده شود.

    توجه داشته باشید که برای دو ویژگی اول مقادیر پیش‌فرض وجود دارد، بنابراین حتی اگر هیچ شیء _options_ به سازنده {{domxref("AudioWorkletNode.AudioWorkletNode", "AudioWorkletNode()")}} ارسال نشود، شیء _options_ که توسط گره به سازنده `AudioWorkletProcessor` ارسال می‌شود وجود خواهد داشت و حداقل دارای `numberOfInputs` و `numberOfOutputs` خواهد بود.

### Return value

نمونه تازه ساخته شده {{domxref("AudioWorkletProcessor")}}.

## Examples

در این مثال، ما گزینه‌های سفارشی را به سازنده {{domxref("AudioWorkletNode.AudioWorkletNode", "AudioWorkletNode()")}} ارسال می‌کنیم و مشاهده می‌کنیم که چگونه یک [کلون ساختاریافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) از آنها به سازنده `AudioWorkletProcessor` ما ارسال می‌شود.

ابتدا باید یک {{domxref("AudioWorkletProcessor")}} سفارشی تعریف کرده و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

```js
// test-processor.js
class TestProcessor extends AudioWorkletProcessor {
  constructor(options) {
    super();
    console.log(options.numberOfInputs);
    console.log(options.processorOptions.someUsefulVariable);
  }
  process(inputs, outputs, parameters) {
    return true;
  }
}

registerProcessor("test-processor", TestProcessor);
```

سپس، در فایل اسکریپت اصلی خود، پردازنده را بارگذاری می‌کنیم، یک نمونه از `AudioWorkletNode` ایجاد کرده و نام پردازنده و شیء _options_ را به آن ارسال می‌کنیم.

در شیء _options_، `processorOptions` را با یک نمونه {{jsxref("Map")}} تحت کلید `someUsefulVariable` ارسال می‌کنیم. ما `numberOfInputs` را ارسال نمی‌کنیم و می‌بینیم که چگونه مقدار پیش‌فرض خود را دریافت می‌کند.

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("test-processor.js");
const testNode = new AudioWorkletNode(audioContext, "test-processor", {
  processorOptions: {
    someUsefulVariable: new Map([
      [1, "one"],
      [2, "two"],
    ]),
  },
});
```

خروجی کنسول به صورت زیر خواهد بود:

```plain
> 1 // AudioWorkletNode options.numberOfInputs set to default
> Map(2) { 1 => "one", 2 => "two" } // A cloned map under someUsefulVariable
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("AudioWorkletNode", "AudioWorkletNode")}} interface