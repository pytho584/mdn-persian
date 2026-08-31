---
title: "BiquadFilterNode: detune property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/detune"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: detune property"
short-title: detune
slug: Web/API/BiquadFilterNode/detune
page-type: web-api-instance-property
browser-compat: api.BiquadFilterNode.detune
---

{{ APIRef("Web Audio API") }}

ویژگی `detune` از رابط {{ domxref("BiquadFilterNode") }} یک {{domxref("AudioParam")}} با [نرخ a](/en-US/docs/Web/API/AudioParam#a-rate) است که نشان‌دهندهٔ تنظیم‌زدایی (detuning) فرکانس بر حسب [سنت](https://en.wikipedia.org/wiki/Cent_%28music%29) می‌باشد.

## مقدار

یک {{domxref("AudioParam")}} با [نرخ a](/en-US/docs/Web/API/AudioParam#a-rate).

> [!NOTE] هرچند `AudioParam` بازگردانده شده فقط‌خواندنی است، اما مقداری که آن نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

مثال زیر کاربرد پایه‌ای یک `AudioContext` برای ایجاد یک گره فیلتر Biquad را نشان می‌دهد. برای مثال‌ها/اطلاعات کاربردی کامل‌تر، نسخهٔ نمایشی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط به [خطوط ۱۰۸ تا ۱۹۳ app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

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
biquadFilter.frequency.value = 1000;
biquadFilter.gain.value = 25;
biquadFilter.detune.value = 100;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)