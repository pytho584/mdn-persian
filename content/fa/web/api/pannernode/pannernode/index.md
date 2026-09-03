---
title: "PannerNode: PannerNode() constructor"
short-title: PannerNode()
slug: Web/API/PannerNode/PannerNode
page-type: web-api-constructor
browser-compat: api.PannerNode.PannerNode
---

{{APIRef("Web Audio API")}}

سازنده **`PannerNode()`** در [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک نمونه جدید از شیء {{domxref("PannerNode")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new PannerNode(context)
new PannerNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("BaseAudioContext")}} که نشان‌دهنده بافت (context) صوتی مورد نظر برای اتصال این گره است.
- `options` {{optional_inline}}
  - : یک شیء دیکشنری از نوع [`PannerOptions`](https://webaudio.github.io/web-audio-api/#idl-def-PannerOptions) که ویژگی‌های مورد نظر برای `PannerNode` را مشخص می‌کند:
    - `panningModel`
      - : {{domxref("PannerNode.panningModel")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `equalpower` است).
    - `distanceModel`
      - : {{domxref("PannerNode.distanceModel")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `inverse` است).
    - `positionX`
      - : {{domxref("PannerNode.positionX")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `0` است).
    - `positionY`
      - : {{domxref("PannerNode.positionY")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `0` است).
    - `positionZ`
      - : {{domxref("PannerNode.positionZ")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `0` است).
    - `orientationX`
      - : {{domxref("PannerNode.orientationX")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `1` است).
    - `orientationY`
      - : {{domxref("PannerNode.orientationY")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `0` است).
    - `orientationZ`
      - : {{domxref("PannerNode.orientationZ")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `0` است).
    - `refDistance`
      - : {{domxref("PannerNode.refDistance")}} مورد نظر برای {{domxref("PannerNode")}}. مقدار پیش‌فرض `1` است و مقادیر منفی مجاز نیستند.
    - `maxDistance`
      - : {{domxref("PannerNode.maxDistance")}} مورد نظر برای {{domxref("PannerNode")}}. مقدار پیش‌فرض `10000` است و مقادیر غیرمثبت (صفر یا منفی) مجاز نیستند.
    - `rolloffFactor`
      - : {{domxref("PannerNode.rolloffFactor")}} مورد نظر برای {{domxref("PannerNode")}}. مقدار پیش‌فرض `1` است و مقادیر منفی مجاز نیستند.
    - `coneInnerAngle`
      - : {{domxref("PannerNode.coneInnerAngle")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `360` است).
    - `coneOuterAngle`
      - : {{domxref("PannerNode.coneOuterAngle")}} مورد نظر برای {{domxref("PannerNode")}} (مقدار پیش‌فرض `360` است).
    - `coneOuterGain`
      - : {{domxref("PannerNode.coneOuterGain")}} مورد نظر برای {{domxref("PannerNode")}}. مقدار پیش‌فرض `0` است و مقدار آن می‌تواند در بازه ۰ تا ۱ باشد.
    - `channelCount`
      - : یک عدد صحیح که مشخص می‌کند هنگام [up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به ورودی‌های گره، از چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی (enumerated) که نحوه تطبیق کانال‌ها بین ورودی و خروجی گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که مفهوم کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر ممکن عبارتند از `"speakers"` یا `"discrete"`. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### استثناها (Exceptions)

- {{jsxref("RangeError")}}
  - : اگر ویژگی‌های `refDistance`، `maxDistance` یا `rolloffFactor` مقداری خارج از محدوده مجاز داشته باشند، این خطا پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر ویژگی `coneOuterGain` مقداری خارج از محدوده مجاز (۰ تا ۱) داشته باشد، این خطا پرتاب می‌شود.

## مثال‌ها

```js
const ctx = new AudioContext();

const options = {
  positionX: 1,
  maxDistance: 5000,
};

const myPanner = new PannerNode(ctx, options);
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}