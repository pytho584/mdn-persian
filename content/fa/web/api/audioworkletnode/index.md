---
title: "AudioWorkletNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletNode"
status: "needs-translation"
---

---
title: AudioWorkletNode
slug: Web/API/AudioWorkletNode
page-type: web-api-interface
browser-compat: api.AudioWorkletNode
---

{{APIRef("Web Audio API")}}{{SecureContext_Header}}

> [!NOTE]
> اگرچه این رابط خارج از [بسترهای امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) در دسترس است، ویژگی {{domxref("BaseAudioContext.audioWorklet")}} در آنجا در دسترس نیست، بنابراین {{domxref("AudioWorkletProcessor")}}های سفارشی نمی‌توانند خارج از آن بسترها تعریف شوند.

رابط **`AudioWorkletNode`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) نشان‌دهندهٔ یک کلاس پایه برای یک {{domxref("AudioNode")}} تعریف‌شده توسط کاربر است که می‌تواند همراه با سایر گره‌ها به یک گراف مسیردهی صوتی متصل شود. این رابط یک {{domxref("AudioWorkletProcessor")}} مرتبط دارد که پردازش واقعی صدا را در یک ریسمان رندر Web Audio انجام می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("AudioWorkletNode.AudioWorkletNode", "AudioWorkletNode()")}}
  - : یک نمونه جدید از یک شیء `AudioWorkletNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("AudioNode")}} را نیز به ارث می‌برد._

- {{domxref("AudioWorkletNode.port")}} {{ReadOnlyInline}}
  - : یک {{domxref("MessagePort")}} برمی‌گرداند که برای ارتباط دوطرفه بین گره و {{domxref("AudioWorkletProcessor")}} مرتبط با آن استفاده می‌شود. انتهای دیگر در ویژگی {{domxref("AudioWorkletProcessor.port", "port")}} پردازنده در دسترس است.
- {{domxref("AudioWorkletNode.parameters")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParamMap")}} برمی‌گرداند — مجموعه‌ای از اشیاء {{domxref("AudioParam")}}. این اشیاء هنگام ایجاد `AudioWorkletProcessor` زیرین نمونه‌سازی می‌شوند. اگر `AudioWorkletProcessor` یک getter ایستا به نام {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} داشته باشد، آرایه {{domxref("AudioParamDescriptor")}} برگشت‌داده‌شده از آن برای ایجاد اشیاء `AudioParam` روی `AudioWorkletNode` استفاده می‌شود. با این سازوکار می‌توان اشیاء `AudioParam` خود را از `AudioWorkletNode` در دسترس قرار داد. سپس می‌توانید مقادیر آن‌ها را در `AudioWorkletProcessor` مرتبط استفاده کنید.

### رویدادها

- {{domxref("AudioWorkletNode.processorerror_event", "processorerror")}}
  - : زمانی که خطایی در {{domxref("AudioWorkletProcessor")}} مرتبط پرتاب شود، فعال می‌شود. پس از فعال شدن، پردازنده و در نتیجه گره تا پایان عمر خود خروجی سکوت خواهند داد.

## روش‌های نمونه

_روش‌های والد خود، {{domxref("AudioNode")}} را نیز به ارث می‌برد._

_رابط `AudioWorkletNode` هیچ روشی از خود تعریف نمی‌کند._

## نمونه‌ها

در این مثال، یک `AudioWorkletNode` سفارشی ایجاد می‌کنیم که نویز تصادفی خروجی می‌دهد.

ابتدا باید یک {{domxref("AudioWorkletProcessor")}} سفارشی تعریف کنیم که نویز تصادفی خروجی بدهد و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

```js
// random-noise-processor.js
class RandomNoiseProcessor extends AudioWorkletProcessor {
  process(inputs, outputs, parameters) {
    const output = outputs[0];
    output.forEach((channel) => {
      for (let i = 0; i < channel.length; i++) {
        channel[i] = Math.random() * 2 - 1;
      }
    });
    return true;
  }
}

registerProcessor("random-noise-processor", RandomNoiseProcessor);
```

سپس، در فایل اسکریپت اصلی خود، پردازنده را بارگذاری می‌کنیم، یک نمونه از `AudioWorkletNode` با ارسال نام پردازنده به آن ایجاد می‌کنیم و گره را به یک گراف صوتی متصل می‌کنیم.

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("random-noise-processor.js");
const randomNoiseNode = new AudioWorkletNode(
  audioContext,
  "random-noise-processor",
);
randomNoiseNode.connect(audioContext.destination);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [استفاده از AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)