---
title: "IIRFilterNode: IIRFilterNode() constructor"
short-title: IIRFilterNode()
slug: Web/API/IIRFilterNode/IIRFilterNode
page-type: web-api-constructor
browser-compat: api.IIRFilterNode.IIRFilterNode
---

{{APIRef("Web Audio API")}}

سازندهٔ **`IIRFilterNode()`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء جدید {{domxref("IIRFilterNode")}} می‌سازد که یک پردازندهٔ {{domxref("AudioNode")}} است و یک فیلتر عمومی با پاسخ ضربهٔ بی‌نهایت (IIR) را پیاده‌سازی می‌کند.

## سینتکس

```js-nolint
new IIRFilterNode(context, options)
```

### پارامترها

- `context`
  - : یک ارجاع به یک {{domxref("AudioContext")}}.
- `options`
  - : گزینه‌ها به شرح زیر هستند:
    - `feedforward`
      - : یک دنباله از ضرایب پیش‌خور (feedforward).
    - `feedback`
      - : یک دنباله از ضرایب بازخورد (feedback).
    - `channelCount`
      - : یک عدد صحیح است که تعیین می‌کند هنگام [up-mixing and down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصال به هر یک از ورودی‌های گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی است که نحوهٔ تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر، از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی است که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که صدا چگونه [up-mixing and down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) خواهد شد. مقادیر ممکن عبارتند از `"speakers"` یا `"discrete"`. (برای اطلاعات بیشتر، از جمله مقادیر پیش‌فرض، به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

برخلاف سایر گره‌ها در Web Audio API، گزینه‌هایی که هنگام ایجاد فیلتر IIR به آن داده می‌شوند اختیاری نیستند. فیلتر برای کار کردن به این مقادیر نیاز دارد و با توجه به طیف گستردهٔ فیلترهای موجود، هیچ مقدار پیش‌فرضی وجود ندارد.

### مقدار بازگشتی

یک نمونهٔ جدید از شیء {{domxref("IIRFilterNode")}}.

## مثال‌ها

```js
let feedForward = [0.00020298, 0.0004059599, 0.00020298];
let feedBackward = [1.0126964558, -1.9991880801, 0.9873035442];

const audioCtx = new AudioContext();

const iirFilter = new IIRFilterNode(audioCtx, {
  feedforward: feedForward,
  feedback: feedBackward,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```