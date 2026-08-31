---
title: "BiquadFilterNode: Q property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/Q"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: Q property"
short-title: Q
slug: Web/API/BiquadFilterNode/Q
page-type: web-api-instance-property
browser-compat: api.BiquadFilterNode.Q
---

{{ APIRef("Web Audio API") }}

خاصیت `Q` از رابط {{ domxref("BiquadFilterNode") }} یک {{domxref("AudioParam")}} از نوع [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) است؛ یک double که نمایانگر [Q factor](https://en.wikipedia.org/wiki/Q_factor) یا _ضریب کیفیت_ است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار {{domxref("AudioParam/defaultValue", "defaultValue")}} آن `1`، و {{domxref("AudioParam/minValue", "minValue")}} و {{domxref("AudioParam/maxValue", "maxValue")}} آن ±(2<sup>128</sup> - 2<sup>104</sup>) یا تقریباً ±3.403e38 است. این بازهٔ اعداد اعشاری با دقت تک‌دقتی (single-precision floating-point) است.

محدودهٔ مقدار واقعی آن به {{domxref("BiquadFilterNode/type", "type")}} فیلتر بستگی دارد:

- برای `lowpass` و `highpass`، مقدار `Q` به‌صورت دسیبل تفسیر می‌شود. برای این فیلترها محدودهٔ مقدار [-Q, Q] است
  که در آن Q بزرگترین مقداری است که برای آن 10<sup>Q/20</sup> از حد بالای ذکرشده سرریز نمی‌کند. این مقدار تقریباً 770.63678 است.
- برای `bandpass`، `notch`، `allpass` و `peaking`، مقدار `Q` به پهنای باند فیلتر مربوط است و باید مثبت باشد، اما حداکثر سخت‌گیرانه‌تری نسبت به مورد بالا وجود ندارد.
- برای فیلترهای `lowshelf` و `highshelf` استفاده نمی‌شود.

> [!NOTE]
> اگرچه `AudioParam` برگشتی فقط‌خواندنی است، اما مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

مثال زیر کاربرد پایهٔ AudioContext برای ایجاد یک گرهٔ فیلتر Biquad را نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) را ببینید (برای کد مرتبط به [app.js lines 108–193](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

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

biquadFilter.type = "peaking";
biquadFilter.frequency.value = 1000;
biquadFilter.Q.value = 100;
biquadFilter.gain.value = 25;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)