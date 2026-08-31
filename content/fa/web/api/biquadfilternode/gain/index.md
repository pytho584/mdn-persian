---
title: "BiquadFilterNode: gain property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/gain"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: gain property"
short-title: gain
slug: Web/API/BiquadFilterNode/gain
page-type: web-api-instance-property
browser-compat: api.BiquadFilterNode.gain
---

{{ APIRef("Web Audio API") }}

ویژگی `gain` در رابط {{ domxref("BiquadFilterNode") }} یک {{domxref("AudioParam")}} با [نرخ a](/en-US/docs/Web/API/AudioParam#a-rate) است — یک عدد double که نشان‌دهنده [بهره](https://en.wikipedia.org/wiki/Gain) (gain) استفاده‌شده در الگوریتم فیلتر فعلی است.

وقتی مقدار آن مثبت باشد، بهره واقعی را نشان می‌دهد؛ وقتی منفی باشد، نشان‌دهنده تضعیف (attenuation) است.

این مقدار بر حسب dB بیان می‌شود، مقدار پیش‌فرض آن `0` است و می‌تواند مقداری در محدوده اسمی `40-` تا `40` بگیرد.

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه `AudioParam` بازگشتی فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

مثال زیر کاربرد پایه‌ای یک AudioContext برای ایجاد یک گره فیلتر Biquad را نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط، [خطوط ۱۰۸ تا ۱۹۳ فایل app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) را ببینید).

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
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)