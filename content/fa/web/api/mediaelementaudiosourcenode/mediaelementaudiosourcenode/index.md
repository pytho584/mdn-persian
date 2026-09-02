---
title: "MediaElementAudioSourceNode: MediaElementAudioSourceNode() constructor"
short-title: MediaElementAudioSourceNode()
slug: Web/API/MediaElementAudioSourceNode/MediaElementAudioSourceNode
page-type: web-api-constructor
browser-compat: api.MediaElementAudioSourceNode.MediaElementAudioSourceNode
---

{{APIRef("Web Audio API")}}

سازنده‌ی **`MediaElementAudioSourceNode()`** یک نمونه‌ی جدید از شیء {{domxref("MediaElementAudioSourceNode")}} می‌سازد.

## Syntax

```js-nolint
new MediaElementAudioSourceNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("AudioContext")}} که نشان‌دهنده‌ی بافت صوتی مورد نظر برای اتصال گره به آن است.
- `options`
  - : یک شیء که ویژگی‌های مورد نظر برای `MediaElementAudioSourceNode` را تعریف می‌کند:
    - `mediaElement`
      - : یک {{domxref("HTMLMediaElement")}} که به عنوان منبع صدا استفاده خواهد شد.
    - `channelCount`
      - : یک عدد صحیح که تعیین می‌کند هنگام [افزایش و کاهش کانال](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به هر ورودی گره، چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : رشته‌ای که نحوه‌ی تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : رشته‌ای که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [افزایش و کاهش کانال](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر احتمالی `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelInterpretation")}} مراجعه کنید.)

### مقدار بازگشتی

یک نمونه‌ی جدید از {{domxref("MediaElementAudioSourceNode")}}.

## نمونه‌ها

```js
const ac = new AudioContext();
const mediaElement = document.createElement("audio");

const myAudioSource = new MediaElementAudioSourceNode(ac, {
  mediaElement,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}