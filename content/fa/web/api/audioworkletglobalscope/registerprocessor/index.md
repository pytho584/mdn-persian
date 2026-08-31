---
title: "AudioWorkletGlobalScope: registerProcessor() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletGlobalScope/registerProcessor"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletGlobalScope: registerProcessor() method"
short-title: registerProcessor()
slug: Web/API/AudioWorkletGlobalScope/registerProcessor
page-type: web-api-instance-method
browser-compat: api.AudioWorkletGlobalScope.registerProcessor
---

{{ APIRef("Web Audio API") }}

متد **`registerProcessor`** از رابط {{domxref("AudioWorkletGlobalScope")}} یک سازنده کلاس مشتق‌شده از رابط {{domxref("AudioWorkletProcessor")}} را تحت یک _نام_ مشخص ثبت می‌کند.

## سینتکس

```js-nolint
registerProcessor(name, processorCtor)
```

### پارامترها

- `name`
  - : رشته‌ای که نامی را نشان می‌دهد که پردازنده با آن ثبت خواهد شد.
- `processorCtor`
  - : سازنده کلاسی مشتق‌شده از {{domxref("AudioWorkletProcessor")}}.

> [!NOTE]
> پس از ثبت پردازنده، یک جفت کلید-مقدار `{ name: constructor }` به صورت داخلی در {{domxref("AudioWorkletGlobalScope")}} ذخیره می‌شود. برای ایجاد یک {{domxref("AudioWorkletNode")}} بر اساس پردازنده ثبت‌شده، باید به _نام_ ارجاع داده شود. یک پردازنده جدید با نام داده‌شده به صورت داخلی ایجاد و با گره جدید مرتبط می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : در شرایط زیر پرتاب می‌شود:
    - _نام_ یک رشته خالی باشد.
    - سازandهای با _نام_ داده‌شده از قبل ثبت شده باشد. ثبت نام یکسان دو بار مجاز نیست.

- {{jsxref("TypeError")}}
  - : در شرایط زیر پرتاب می‌شود:
    - _processorCtor_ یک سازنده قابل فراخوانی نباشد.
    - ویژگی {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} سازنده وجود داشته باشد و آرایه‌ای از اشیاء مبتنی بر {{domxref("AudioParamDescriptor")}} برنگرداند.

## مثال‌ها

در این مثال، یک `AudioWorkletNode` سفارشی می‌سازیم که خروجی آن سکوت است.

ابتدا باید یک {{domxref("AudioWorkletProcessor")}} سفارشی تعریف کرده و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

```js
// test-processor.js
class TestProcessor extends AudioWorkletProcessor {
  process(inputs, outputs, parameters) {
    return true;
  }
}

registerProcessor("test-processor", TestProcessor);
```

سپس، در فایل اسکریپت اصلی خود، پردازنده را بارگذاری می‌کنیم، یک نمونه از `AudioWorkletNode` ایجاد می‌کنیم — نام پردازنده‌ای را که هنگام فراخوانی `registerProcessor` استفاده کردیم به آن می‌دهیم — و آن را به یک گراف صوتی متصل می‌کنیم.

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("test-processor.js");
const node = new AudioWorkletNode(audioContext, "test-processor");
node.connect(audioContext.destination);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)