---
title: "BaseAudioContext: createChannelSplitter() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createChannelSplitter"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createChannelSplitter() method"
short-title: createChannelSplitter()
slug: Web/API/BaseAudioContext/createChannelSplitter
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createChannelSplitter
---

{{ APIRef("Web Audio API") }}

متد `createChannelSplitter()` از رابط {{domxref("BaseAudioContext")}} برای ایجاد یک {{domxref("ChannelSplitterNode")}} استفاده می‌شود که به شما امکان می‌دهد کانال‌های جداگانه یک جریان صوتی را دسترسی و پردازش کنید.

> [!NOTE]
> سازنده {{domxref("ChannelSplitterNode.ChannelSplitterNode", "ChannelSplitterNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("ChannelSplitterNode")}} است؛ برای اطلاعات بیشتر به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## Syntax

```js-nolint
createChannelSplitter(numberOfOutputs)
```

### Parameters

- `numberOfOutputs`
  - : تعداد کانال‌های جریان صوتی ورودی که می‌خواهید به‌صورت جداگانه خروجی بگیرید؛ اگر این پارامتر مشخص نشود، مقدار پیش‌فرض ۶ است.

### Return value

یک {{domxref("ChannelSplitterNode")}}.

## Examples

مثال ساده زیر نشان می‌دهد که چگونه می‌توانید یک استریو (مثلاً یک قطعه موسیقی) را جدا کنید و کانال چپ و راست را به‌طور متفاوت پردازش کنید. برای استفاده از آنها، باید از پارامتر دوم و سوم متد {{domxref("AudioNode/connect", "AudioNode.connect(AudioNode)")}} استفاده کنید که به شما امکان می‌دهد اندیس کانال مبدأ و اندیس کانال مقصد را مشخص کنید.

```js
const ac = new AudioContext();
ac.decodeAudioData(someStereoBuffer, (data) => {
  const source = ac.createBufferSource();
  source.buffer = data;
  const splitter = ac.createChannelSplitter(2);
  source.connect(splitter);
  const merger = ac.createChannelMerger(2);

  // Reduce the volume of the left channel only
  const gainNode = ac.createGain();
  gainNode.gain.setValueAtTime(0.5, ac.currentTime);
  splitter.connect(gainNode, 0);

  // Connect the splitter back to the second input of the merger: we
  // effectively swap the channels, here, reversing the stereo image.
  gainNode.connect(merger, 0, 1);
  splitter.connect(merger, 1, 0);

  const dest = ac.createMediaStreamDestination();

  // Because we have used a ChannelMergerNode, we now have a stereo
  // MediaStream we can use to pipe the Web Audio graph to WebRTC,
  // MediaRecorder, etc.
  merger.connect(dest);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)