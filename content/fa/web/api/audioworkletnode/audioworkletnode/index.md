---
title: "AudioWorkletNode: AudioWorkletNode() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletNode/AudioWorkletNode"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletNode: AudioWorkletNode() constructor"
short-title: AudioWorkletNode()
slug: Web/API/AudioWorkletNode/AudioWorkletNode
page-type: web-api-constructor
browser-compat: api.AudioWorkletNode.AudioWorkletNode
---

{{APIRef("Web Audio API")}}{{SecureContext_Header}}

سازندهٔ **`AudioWorkletNode()`** یک شیء جدید {{domxref("AudioWorkletNode")}} می‌سازد که نمایانگر یک {{domxref("AudioNode")}} است که از یک تابع جاوااسکریپت برای پردازش صوتی سفارشی استفاده می‌کند.

## نحو

```js-nolint
new AudioWorkletNode(context, name)
new AudioWorkletNode(context, name, options)
```

### پارامترها

- `context`
  - : نمونهٔ {{domxref("BaseAudioContext")}} که این گره با آن مرتبط خواهد شد.
- `name`
  - : یک رشته که نام {{domxref("AudioWorkletProcessor")}} را نشان می‌دهد که این گره بر اساس آن ساخته می‌شود. پردازنده‌ای با نام داده‌شده باید ابتدا با استفاده از متد {{domxref("AudioWorkletGlobalScope.registerProcessor()")}} ثبت شده باشد.
- `options` {{optional_inline}}
  - : یک شیء حاوی صفر یا چند ویژگی اختیاری زیر برای پیکربندی گرهٔ جدید:

    <!-- The specification refers to this object as: AudioWorkletNodeOptions -->

    > [!NOTE]
    > نتیجهٔ [الگوریتم شبیه‌سازی ساخت‌یافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) اعمال‌شده روی این شیء نیز به‌صورت داخلی به سازندهٔ {{domxref("AudioWorkletProcessor.AudioWorkletProcessor", "AudioWorkletProcessor()")}} مرتبط ارسال می‌شود — این امکان را می‌دهد که مقداردهی اولیهٔ سفارشی برای یک {{domxref("AudioWorkletProcessor")}} تعریف‌شده توسط کاربر انجام شود.
    - `numberOfInputs` {{optional_inline}}
      - : مقداردهی اولیهٔ ویژگی {{domxref("AudioNode.numberOfInputs", "numberOfInputs")}}. پیش‌فرض 1 است.
    - `numberOfOutputs` {{optional_inline}}
      - : مقداردهی اولیهٔ ویژگی {{domxref("AudioNode.numberOfOutputs", "numberOfOutputs")}}. پیش‌فرض 1 است.
    - `outputChannelCount` {{optional_inline}}
      - : یک **آرایه** که تعداد کانال‌ها را برای هر خروجی تعریف می‌کند. برای مثال، _outputChannelCount: \[n, m]_ تعداد کانال‌ها را در خروجی اول برابر _n_ و در خروجی دوم برابر _m_ مشخص می‌کند. طول آرایه باید با `numberOfOutputs` مطابقت داشته باشد.
    - `parameterData` {{optional_inline}}
      - : یک شیء حاوی مقادیر اولیهٔ اشیاء {{domxref("AudioParam")}} سفارشی روی این گره (در ویژگی {{domxref("AudioWorkletNode.parameters", "parameters")}} آن)، که `key` نام یک پارامتر سفارشی و `value` مقدار اولیهٔ آن است.
    - `processorOptions` {{optional_inline}}
      - : هر دادهٔ اضافی که می‌تواند برای مقداردهی اولیهٔ سفارشی {{domxref("AudioWorkletProcessor")}} پایه استفاده شود.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : مقدار `options.outputChannelCount` مشخص‌شده برابر 0 یا بزرگ‌تر از مقداری است که پیاده‌سازی فعلی پشتیبانی می‌کند.

    هر دو `options.numberOfInputs` و `options.numberOfOutputs` برابر 0 هستند.

- `IndexSizeError` {{domxref("DOMException")}}
  - : طول آرایهٔ `options.outputChannelCount` با `options.numberOfOutputs` مطابقت ندارد.

## نکات استفاده

مقادیر مختلف پارامتر `options` می‌توانند اثرات زیر را داشته باشند.

اگر تعداد ورودی‌ها و تعداد خروجی‌ها هر دو روی 0 تنظیم شوند، یک `NotSupportedError` پرتاب می‌شود و فرایند ساخت گره متوقف می‌شود. اگر طول آرایهٔ `outputChannelCount` با `numberOfOutputs` مطابقت نداشته باشد، یک `IndexSizeError` {{domxref("DOMException")}} پرتاب می‌شود.

اگر `outputChannelCount` مشخص نشده باشد و `numberOfInputs` و `numberOfOutputs` هر دو 1 باشند، تعداد کانال اولیهٔ `AudioWorkletNode` روی 1 تنظیم می‌شود. این اثر باعث می‌شود تعداد کانال‌های خروجی به‌صورت پویا به تعداد کانال‌های محاسبه‌شده تغییر کند، بر اساس تعداد کانال ورودی و تنظیمات فعلی ویژگی {{domxref("AudioNode")}} به نام {{domxref("AudioNode.channelCountMode", "channelCountMode")}}.

در غیر این صورت، اگر `outputChannelCount` ارائه شده باشد _و_ مقادیر `numberOfInputs` و `numberOfOutputs` هر دو 1 باشند، تعداد کانال‌های گرهٔ کار صوتی به مقدار `outputChannelCount` تنظیم می‌شود. در غیر این صورت، تعداد کانال‌های هر کانال در مجموعهٔ کانال‌های خروجی به‌گونه‌ای تنظیم می‌شود که با مقدار متناظر در آرایهٔ `outputChannelCount` مطابقت داشته باشد.

## مثال‌ها

_برای یک مثال کامل که پردازش صوتی تعریف‌شده توسط کاربر را نشان می‌دهد، صفحهٔ {{domxref("AudioWorkletNode")}} را ببینید._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [پردازش صوتی پس‌زمینه با استفاده از AudioWorklet](/en-US/docs/Web/API/Web_Audio_API/Using_AudioWorklet)
- رابط {{domxref("AudioWorkletNode", "AudioWorkletNode")}}