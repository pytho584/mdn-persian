---
title: "BaseAudioContext: createBiquadFilter() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createBiquadFilter"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createBiquadFilter() method"
short-title: createBiquadFilter()
slug: Web/API/BaseAudioContext/createBiquadFilter
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createBiquadFilter
---

{{ APIRef("Web Audio API") }}

روش `createBiquadFilter()` از رابط {{ domxref("BaseAudioContext") }} یک {{ domxref("BiquadFilterNode") }} ایجاد می‌کند که یک فیلتر مرتبه دوم را نشان می‌دهد که به‌عنوان چندین نوع فیلتر رایج مختلف قابل پیکربندی است.

> [!NOTE]
> سازنده {{domxref("BiquadFilterNode.BiquadFilterNode", "BiquadFilterNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("BiquadFilterNode")}} است؛ برای اطلاعات بیشتر به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## نحو

```js-nolint
createBiquadFilter()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("BiquadFilterNode")}}.

## مثال‌ها

مثال زیر کاربرد پایه یک AudioContext را برای ایجاد یک گره فیلتر Biquad نشان می‌دهد. برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط به [خطوط ۱۰۸ تا ۱۹۳ app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

```js
const audioCtx = new AudioContext();

// Set up the different audio nodes we will use for the app
const analyser = audioCtx.createAnalyser();
const distortion = audioCtx.createWaveShaper();
const gainNode = audioCtx.createGain();
const biquadFilter = audioCtx.createBiquadFilter();
const convolver = audioCtx.createConvolver();

// Connect the nodes together

source = audioCtx.createMediaStreamSource(stream);
source.connect(analyser);
analyser.connect(distortion);
distortion.connect(biquadFilter);
biquadFilter.connect(convolver);
convolver.connect(gainNode);
gainNode.connect(audioCtx.destination);

// Manipulate the Biquad filter

biquadFilter.type = "lowshelf";
biquadFilter.frequency.setValueAtTime(1000, audioCtx.currentTime);
biquadFilter.gain.setValueAtTime(25, audioCtx.currentTime);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)