---
title: "BaseAudioContext: createChannelMerger() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createChannelMerger"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createChannelMerger() method"
short-title: createChannelMerger()
slug: Web/API/BaseAudioContext/createChannelMerger
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createChannelMerger
---

{{ APIRef("Web Audio API") }}

متد `createChannelMerger()` از رابط {{domxref("BaseAudioContext")}} یک {{domxref("ChannelMergerNode")}} ایجاد می‌کند که کانال‌های جریان‌های صوتی متعدد را در یک جریان صوتی واحد ترکیب می‌کند.

> [!NOTE]
> سازندهٔ {{domxref("ChannelMergerNode.ChannelMergerNode", "ChannelMergerNode()")}} روش توصیه‌شده برای ایجاد یک
> {{domxref("ChannelMergerNode")}} است؛ به
> [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## سینتکس

```js-nolint
createChannelMerger(numberOfInputs)
```

### پارامترها

- `numberOfInputs`
  - : تعداد کانال‌های جریان‌های صوتی ورودی که جریان خروجی شامل آن‌ها خواهد بود؛
    اگر این پارامتر مشخص نشود، پیش‌فرض ۶ است.

### مقدار بازگشتی

یک {{domxref("ChannelMergerNode")}}.

## مثال‌ها

مثال زیر نشان می‌دهد که چگونه می‌توانید یک تراک استریو (مثلاً یک قطعه موسیقی) را جدا کنید و کانال چپ و راست را به‌طور متفاوت پردازش کنید. برای استفاده از آن‌ها، باید از پارامترهای دوم و سوم متد {{domxref("AudioNode/connect", "AudioNode.connect(AudioNode)")}} استفاده کنید، که به شما امکان می‌دهند هم ایندکس کانال مبدأ و هم ایندکس کانال مقصد را مشخص کنید.

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)