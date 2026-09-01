---
title: "GainNode: GainNode() constructor"
short-title: GainNode()
slug: Web/API/GainNode/GainNode
page-type: web-api-constructor
browser-compat: api.GainNode.GainNode
---

{{APIRef("Web Audio API")}}

**`GainNode()`** سازنده‌ی [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء {{domxref("GainNode")}} جدید می‌سازد که یک {{domxref("AudioNode")}} است و تغییر در بلندی صدا را نشان می‌دهد.

## نحو (Syntax)

```js-nolint
new GainNode(context, options)
```

### پارامترها

- `context`
  - : ارجاعی به یک {{domxref("BaseAudioContext")}}، مانند یک {{domxref("AudioContext")}}.
- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `gain`
      - : میزان بهره‌ای که اعمال می‌شود. این پارامتر یک `rate` است و محدوده‌ی اسمی آن (-∞,+∞) می‌باشد. مقدار پیش‌فرض `1` است.
    - `channelCount`
      - : عددی صحیح است که تعیین می‌کند هنگام [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) در اتصالات به ورودی‌های گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) نحوه استفاده و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی است که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی است که معنای کانال‌ها را توصیف می‌کند. این تفسیر تعیین می‌کند که [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelInterpretation")}} مراجعه کنید.)

### مقدار بازگشتی

یک نمونه‌ی جدید از شیء {{domxref("GainNode")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
