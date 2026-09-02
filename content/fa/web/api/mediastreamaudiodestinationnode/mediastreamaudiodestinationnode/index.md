```markdown
---
title: "MediaStreamAudioDestinationNode: MediaStreamAudioDestinationNode() constructor"
short-title: MediaStreamAudioDestinationNode()
slug: Web/API/MediaStreamAudioDestinationNode/MediaStreamAudioDestinationNode
page-type: web-api-constructor
browser-compat: api.MediaStreamAudioDestinationNode.MediaStreamAudioDestinationNode
---

{{APIRef("Web Audio API")}}

سازنده **`MediaStreamAudioDestinationNode()`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک نمونه جدید از شیء {{domxref("MediaStreamAudioDestinationNode")}} ایجاد می‌کند.

## نحو

```js-nolint
new MediaStreamAudioDestinationNode(context)
new MediaStreamAudioDestinationNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("AudioContext")}} که نشان‌دهنده زمینه صوتی مورد نظر برای اتصال گره است.
- `options` {{optional_inline}}
  - : یک شیء که ویژگی‌های مورد نظر برای `MediaStreamAudioDestinationNode` را تعریف می‌کند:
    - `channelCount`
      - : یک عدد صحیح که برای تعیین تعداد کانال‌ها در هنگام
        [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing)
        اتصالات به ورودی‌های گره استفاده می‌شود. (برای اطلاعات بیشتر به
        {{domxref("AudioNode.channelCount")}} مراجعه کنید.) نحوه استفاده و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک رشته که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک رشته که معنای کانال‌ها را توصیف می‌کند. این تفسیر نحوه انجام
        [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing)
        صدا را تعیین می‌کند. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

## مثال‌ها

```js
const ac = new AudioContext();

const myDestination = new MediaStreamAudioDestinationNode(ac);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```