---
title: "OscillatorNode: OscillatorNode() constructor"
short-title: OscillatorNode()
slug: Web/API/OscillatorNode/OscillatorNode
page-type: web-api-constructor
browser-compat: api.OscillatorNode.OscillatorNode
---

{{APIRef("Web Audio API")}}

سازنده‌ی **`OscillatorNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء {{domxref("OscillatorNode")}} جدید می‌سازد که یک {{domxref("AudioNode")}} است و یک شکل‌موج دوره‌ای مانند موج سینوسی را نشان می‌دهد. به‌صورت اختیاری می‌توانید مقادیر ویژگی‌های این گره را طوری تنظیم کنید که با مقادیر موجود در یک شیء مشخص هماهنگ باشند.

اگر مقادیر پیش‌فرض ویژگی‌ها برایتان قابل قبول است، می‌توانید به‌جای آن از متد factory به نام {{domxref("BaseAudioContext.createOscillator()")}} استفاده کنید؛ همچنین ببینید [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode).

## Syntax

```js-nolint
new OscillatorNode(context, options)
```

### Parameters

- `context`
  - : ارجاعی به یک {{domxref("AudioContext")}}.
- `options` {{optional_inline}}
  - : شیءای که ویژگی‌های آن مقادیر اولیه‌ی ویژگی‌های گره‌ی نوسان‌ساز را مشخص می‌کنند. هر ویژگی که در این شیء ذکر نشود، مقدار پیش‌فرض مستند خود را خواهد گرفت.
    - `type`
      - : شکل موج تولیدشده توسط گره. مقادیر معتبر عبارت‌اند از `"sine"`، `"square"`، `"sawtooth"`، `"triangle"` و `"custom"`. مقدار پیش‌فرض `"sine"` است.
    - `detune`
      - : مقدار انحراف گام (بر حسب سنت) که `frequency` را به‌اندازه‌ی مشخصی جابه‌جا می‌کند. پیش‌فرض آن 0 است.
    - `frequency`
      - : فرکانس شکل‌موج دوره‌ای (بر حسب [هرتز](https://en.wikipedia.org/wiki/Hertz)). پیش‌فرض آن 440 است.
    - `periodicWave`
      - : یک شکل‌موج دوره‌ای دلخواه که توسط یک شیء {{domxref("PeriodicWave")}} توصیف می‌شود.
    - `channelCount`
      - : یک عدد صحیح که تعیین می‌کند هنگام [بالابردن و پایین‌آوردن تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) در اتصال‌ها به ورودی‌های گره، چه تعداد کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی که نحوه‌ی تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [بالابردن و پایین‌آوردن تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) در صدا چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### Return value

یک نمونه‌ی جدید از شیء {{domxref("OscillatorNode")}}.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}