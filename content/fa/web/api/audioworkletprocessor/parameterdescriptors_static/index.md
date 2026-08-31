---
title: "AudioWorkletProcessor: parameterDescriptors static property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletProcessor/parameterDescriptors_static"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletProcessor: parameterDescriptors static property"
short-title: parameterDescriptors
slug: Web/API/AudioWorkletProcessor/parameterDescriptors_static
page-type: web-api-static-property
spec-urls: https://webaudio.github.io/web-audio-api/#audioworkletprocess-callback-parameters
---

{{APIRef("Web Audio API")}}

ویژگی فقط‌خواندنی **`parameterDescriptors`** از کلاس مشتق‌شده از {{domxref("AudioWorkletProcessor")}} یک _getter ایستا_ است که یک تکرارپذیر از اشیاء مبتنی بر {{domxref("AudioParamDescriptor")}} برمی‌گرداند.

این ویژگی بخشی از رابط {{domxref("AudioWorkletProcessor")}} نیست، اما اگر تعریف شده باشد، به‌صورت داخلی توسط سازندهٔ {{domxref("AudioWorkletProcessor")}} فراخوانی می‌شود تا فهرستی از اشیاء سفارشی {{domxref("AudioParam")}} را در ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} از {{domxref("AudioWorkletNode")}} مرتبط ایجاد کند.

تعریف این getter اختیاری است.

## مقدار

یک تکرارپذیر از اشیاء مبتنی بر {{domxref("AudioParamDescriptor")}}. ویژگی‌های این اشیاء به شرح زیر هستند:

- `name`
  - رشته‌ای که نام `AudioParam` را نشان می‌دهد. با این نام، `AudioParam` در ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} گره در دسترس خواهد بود و با این نام، متد {{domxref("AudioWorkletProcessor.process")}} مقادیر محاسبه‌شدهٔ این `AudioParam` را دریافت خواهد کرد.
- `automationRate` {{optional_inline}}
  - یک رشته از [`"a-rate"`](/en-US/docs/Web/API/AudioParam#a-rate) یا [`"k-rate"`](/en-US/docs/Web/API/AudioParam#k-rate) که نرخ خودکارسازی (automation rate) این `AudioParam` را نشان می‌دهد. پیش‌فرض `"a-rate"` است.
- `minValue` {{optional_inline}}
  - یک `float` که حداقل مقدار `AudioParam` را نشان می‌دهد. پیش‌فرض `-3.4028235e38` است.
- `maxValue` {{optional_inline}}
  - یک `float` که حداکثر مقدار `AudioParam` را نشان می‌دهد. پیش‌فرض `3.4028235e38` است.
- `defaultValue` {{optional_inline}}
  - یک `float` که مقدار اولیهٔ `AudioParam` را نشان می‌دهد. پیش‌فرض `0` است.

## مثال‌ها

برای نمونه‌کد نحوه افزودن getter ایستای `parameterDescriptors` به یک `AudioWorkletProcessor` سفارشی، به [`AudioWorkletNode.parameters`](/en-US/docs/Web/API/AudioWorkletNode/parameters#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)