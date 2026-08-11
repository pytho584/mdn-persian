---
title: "AnalyserNode: AnalyserNode() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/AnalyserNode"
translated_by: "n8n + AI"
---

# AnalyserNode: سازنده AnalyserNode()

سازنده **`AnalyserNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک نمونه جدید از شیء {{domxref("AnalyserNode")}} ایجاد می‌کند.

## Syntax

```js-nolint
new AnalyserNode(context)
new AnalyserNode(context, options)
```

### Parameters

- `context`
  - : یک ارجاع به {{domxref("AudioContext")}} یا {{domxref("OfflineAudioContext")}}.
- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر (همه اختیاری):
    - `fftSize`
      - : اندازه اولیه دلخواه [FFT](https://en.wikipedia.org/wiki/Fast_Fourier_transform) برای تحلیل در [حوزه فرکانس](https://en.wikipedia.org/wiki/Frequency_domain). مقدار پیش‌فرض `2048` است.
    - `maxDecibels`
      - : حداکثر توان اولیه دلخواه بر حسب [دسی‌بل](https://en.wikipedia.org/wiki/Decibel) برای تحلیل FFT. مقدار پیش‌فرض `-30` است.
    - `minDecibels`
      - : حداقل توان اولیه دلخواه بر حسب دسی‌بل برای تحلیل FFT. مقدار پیش‌فرض `-100` است.
    - `smoothingTimeConstant`
      - : ثابت هموارسازی اولیه دلخواه برای تحلیل FFT. مقدار پیش‌فرض `0.8` است.
    - `channelCount`
      - : یک عدد صحیح که مشخص می‌کند هنگام [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) (up-mixing and down-mixing) در اتصالات به ورودی‌های گره، چند کانال استفاده می‌شود. (برای جزئیات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) نحوه استفاده و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار [عددی شمارشی](/en-US/docs/Glossary/Enumerated) که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که معنای کانال‌ها را مشخص می‌کند. این تفسیر تعیین می‌کند که عملیات [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

## See also

- {{domxref("BaseAudioContext.createAnalyser()")}}، متد factory معادل