---
title: "DelayNode: DelayNode() constructor"
short-title: DelayNode()
slug: Web/API/DelayNode/DelayNode
page-type: web-api-constructor
browser-compat: api.DelayNode.DelayNode
---

{{APIRef("Web Audio API")}}

سازنده‌ی **`DelayNode()`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء جدید {{domxref("DelayNode")}} با یک خط تأخیر (delay-line) ایجاد می‌کند؛ یک ماژول پردازش صوتی AudioNode که باعث ایجاد تأخیر بین رسیدن داده‌ی ورودی و انتشار آن به خروجی می‌شود.

## Syntax

```js-nolint
new DelayNode(context)
new DelayNode(context, options)
```

### Parameters

- `context`
  - : یک ارجاع به یک {{domxref("AudioContext")}} یا {{domxref("OfflineAudioContext")}}.
- `options` {{optional_inline}}
  - : یک شیء که گزینه‌های گره تأخیر را مشخص می‌کند. می‌تواند شامل اعضای زیر باشد:
    - `delayTime`
      - : زمان تأخیر اولیه برای گره، بر حسب ثانیه. پیش‌فرض `0` است.
    - `maxDelayTime`
      - : حداکثر زمان تأخیر برای گره، بر حسب ثانیه. پیش‌فرض `1` است.
    - `channelCount`
      - : یک عدد صحیح که برای تعیین تعداد کانال‌های استفاده‌شده هنگام [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به هر ورودی گره به کار می‌رود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که معنی کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### Return value

یک نمونه شیء جدید {{domxref("DelayNode")}}.

## Examples

```js
const audioCtx = new AudioContext();
const delayNode = new DelayNode(audioCtx, {
  delayTime: 0.5,
  maxDelayTime: 2,
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}