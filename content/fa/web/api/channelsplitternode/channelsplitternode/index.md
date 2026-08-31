---
title: "ChannelSplitterNode: ChannelSplitterNode() constructor"
short-title: ChannelSplitterNode()
slug: Web/API/ChannelSplitterNode/ChannelSplitterNode
page-type: web-api-constructor
browser-compat: api.ChannelSplitterNode.ChannelSplitterNode
---

{{APIRef("Web Audio API")}}سازندهٔ **`ChannelSplitterNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک نمونهٔ جدید از شیء {{domxref("ChannelSplitterNode")}} می‌سازد؛ گره‌ای که ورودی را به تعداد خروجی‌های جداگانه به تعداد کانال‌های صوتی گرهٔ منبع تقسیم می‌کند.

## Syntax

```js-nolint
new ChannelSplitterNode(context)
new ChannelSplitterNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("BaseAudioContext")}} که نشان‌دهندهٔ بافت صوتی مورد نظر برای اتصال گره به آن است.
- `options` {{optional_inline}}
  - : شیءای که ویژگی‌های مورد نظر برای `ChannelSplitterNode` را تعریف می‌کند:
    - `numberOfOutputs` {{optional_inline}}
      - : عددی که تعداد خروجی‌های {{domxref("ChannelSplitterNode")}} را مشخص می‌کند. اگر مشخص نشود، مقدار پیش‌فرض ۶ است.
    - `channelCount` {{optional_inline}}
      - : یک عدد صحیح که تعیین می‌کند هنگام [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) در اتصالات ورودی‌های گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode` {{optional_inline}}
      - : رشته‌ای که نحوهٔ تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation` {{optional_inline}}
      - : رشته‌ای که معنای کانال‌ها را توصیف می‌کند. این تفسیر تعیین می‌کند که [افزایش و کاهش تعداد کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) چگونه انجام شود. مقادیر ممکن عبارت‌اند از `"speakers"` یا `"discrete"`. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### مقدار بازگشتی

یک نمونهٔ جدید از شیء {{domxref("ChannelSplitterNode")}}.

## مثال‌ها

```js
const ac = new AudioContext();

const options = {
  numberOfOutputs: 2,
};

const mySplitter = new ChannelSplitterNode(ac, options);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}