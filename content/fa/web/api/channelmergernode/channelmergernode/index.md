---
title: "ChannelMergerNode: ChannelMergerNode() constructor"
short-title: ChannelMergerNode()
slug: Web/API/ChannelMergerNode/ChannelMergerNode
page-type: web-api-constructor
browser-compat: api.ChannelMergerNode.ChannelMergerNode
---

{{APIRef("Web Audio API")}}

سازندهٔ **`ChannelMergerNode()`** یک نمونهٔ جدید از شیء {{domxref("ChannelMergerNode")}} می‌سازد.

## نحو (Syntax)

```js-nolint
new ChannelMergerNode(context)
new ChannelMergerNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("BaseAudioContext")}} که زمینهٔ صوتی مورد نظر برای مرتبط‌سازی گره با آن را نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء که ویژگی‌های مورد نظر شما برای `ChannelMergerNode` را تعریف می‌کند:
    - `numberOfInputs` {{optional_inline}}
      - : عددی که تعداد ورودی‌های {{domxref("ChannelMergerNode")}} را تعیین می‌کند. اگر مشخص نشود، مقدار پیش‌فرض ۶ استفاده می‌شود.
    - `channelCount` {{optional_inline}}
      - : یک عدد صحیح که تعیین می‌کند هنگام [بالاکشی و پایین‌کشی](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به هر ورودی گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode` {{optional_inline}}
      - : رشته‌ای که نحوهٔ تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر، از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation` {{optional_inline}}
      - : رشته‌ای که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [بالاکشی و پایین‌کشی](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر، از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### مقدار بازگشتی

یک نمونهٔ جدید از شیء {{domxref("ChannelMergerNode")}}.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که گزینه‌ای مانند `channelCount` یا `channelCountMode` مقدار نامعتبری داده شده باشد.

## مثال‌ها

```js
const ac = new AudioContext();

const options = {
  numberOfInputs: 2,
};

const myMerger = new ChannelMergerNode(ac, options);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}