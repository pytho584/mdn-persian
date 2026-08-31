---
title: "BiquadFilterNode: frequency property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/frequency"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: frequency property"
short-title: frequency
slug: Web/API/BiquadFilterNode/frequency
page-type: web-api-instance-property
browser-compat: api.BiquadFilterNode.frequency
---

{{ APIRef("Web Audio API") }}

ویژگی `frequency` در رابط {{ domxref("BiquadFilterNode") }} یک {{domxref("AudioParam")}} با نرخ [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) است — یک عدد اعشاری که فرکانس را در الگوریتم فیلتر فعلی بر حسب هرتز (Hz) نشان می‌دهد.

مقدار پیش‌فرض آن `350` است، با محدوده اسمی از `10` تا [فرکانس نایکوئیست](https://en.wikipedia.org/wiki/Nyquist_frequency) — یعنی نصف نرخ نمونه‌برداری.

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه `AudioParam` برگشتی فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

مثال زیر کاربرد پایه‌ای AudioContext را برای ایجاد یک گره فیلتر Biquad نشان می‌دهد.
برای یک مثال کامل و قابل اجرا، نسخه نمایشی [voice-change-o-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) ما را ببینید (و همچنین [کد منبع](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) را بررسی کنید).

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