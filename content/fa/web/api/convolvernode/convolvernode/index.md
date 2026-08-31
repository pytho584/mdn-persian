---
title: "ConvolverNode: ConvolverNode() constructor"
short-title: ConvolverNode()
slug: Web/API/ConvolverNode/ConvolverNode
page-type: web-api-constructor
browser-compat: api.ConvolverNode.ConvolverNode
---

{{APIRef("Web Audio API")}}

**`ConvolverNode()`** سازنده‌ی [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک نمونه‌ی جدید از شیء {{domxref("ConvolverNode")}} ایجاد می‌کند.

## Syntax

```js-nolint
new ConvolverNode(context, options)
```

### Parameters

- `context`
  - : ارجاعی به یک {{domxref("AudioContext")}}.
- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `buffer`
      - : یک {{domxref("AudioBuffer")}} مونو، استریو یا ۴ کاناله که حاوی پاسخ ضربه‌ای (impulse response) (احتمالاً چندکاناله) است که `ConvolverNode` برای ایجاد افکت ریورب از آن استفاده می‌کند.
    - `disableNormalization`
      - : یک مقدار بولی که کنترل می‌کند آیا پاسخ ضربه‌ای از بافر با نرمال‌سازی توان برابر مقیاس می‌شود یا خیر. مقدار پیش‌فرض `false` است.
    - `channelCount`
      - : یک عدد صحیح که تعیین می‌کند هنگام [افزایش و کاهش کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) برای اتصال به هر ورودی گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [افزایش و کاهش کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### Return value

یک نمونه‌ی جدید از شیء {{domxref("ConvolverNode")}}.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر {{domxref("AudioBuffer")}} ارجاع‌داده‌شده تعداد کانال‌های صحیح را نداشته باشد، یا نرخ نمونه‌برداری آن با {{domxref("AudioContext")}} مرتبط متفاوت باشد، پرتاب می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}