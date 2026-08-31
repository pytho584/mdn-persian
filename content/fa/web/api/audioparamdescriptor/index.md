---
title: "AudioParamDescriptor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParamDescriptor"
translated_by: "n8n + AI"
---

---
title: AudioParamDescriptor
slug: Web/API/AudioParamDescriptor
page-type: web-api-interface
spec-urls: https://webaudio.github.io/web-audio-api/#AudioParamDescriptor
---

{{APIRef("Web Audio API")}}

دیکشنری **`AudioParamDescriptor`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) ویژگی‌های اشیاء {{domxref("AudioParam")}} را مشخص می‌کند.

از آن برای ایجاد `AudioParam` های سفارشی روی یک {{domxref("AudioWorkletNode")}} استفاده می‌شود. اگر {{domxref("AudioWorkletProcessor")}} زیرین دارای یک getter استاتیک {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} باشد، آرایه‌ی اشیاء برگشتی بر اساس این دیکشنری به صورت داخلی توسط سازنده‌ی `AudioWorkletNode` برای پر کردن ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} آن استفاده می‌شود.

## ویژگی‌های نمونه

- `name`
  - : رشته‌ای که نام `AudioParam` را نشان می‌دهد. با این نام، `AudioParam` در ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} گره در دسترس خواهد بود و با این نام، متد {{domxref("AudioWorkletProcessor.process")}} مقادیر محاسبه‌شده‌ی این `AudioParam` را دریافت می‌کند.
- `automationRate` {{optional_inline}}
  - : رشته‌ای که یا [`"a-rate"`](/en-US/docs/Web/API/AudioParam#a-rate) است یا [`"k-rate"`](/en-US/docs/Web/API/AudioParam#k-rate) که نرخ اتوماسیون این `AudioParam` را نشان می‌دهد. پیش‌فرض `"a-rate"` است.
- `minValue` {{optional_inline}}
  - : یک `float` که حداقل مقدار `AudioParam` را نشان می‌دهد. پیش‌فرض `-3.4028235e38` است.
- `maxValue` {{optional_inline}}
  - : یک `float` که حداکثر مقدار `AudioParam` را نشان می‌دهد. پیش‌فرض `3.4028235e38` است.
- `defaultValue` {{optional_inline}}
  - : یک `float` که مقدار اولیه‌ی `AudioParam` را نشان می‌دهد. پیش‌فرض `0` است.

## مثال‌ها

قطعه کد زیر توصیفگری از این نوع را نشان می‌دهد که توسط یک متد استاتیک {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} تعریف‌شده در یک `AudioWorkletProcessor` سفارشی بازگردانده می‌شود (این بخشی از مثال کامل‌تر در [AudioWorkletNode.parameters](/en-US/docs/Web/API/AudioWorkletNode/parameters#examples) است).

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

  // …
}
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)