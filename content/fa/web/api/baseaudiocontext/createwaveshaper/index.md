---
title: "BaseAudioContext: createWaveShaper() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createWaveShaper"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createWaveShaper() method"
short-title: createWaveShaper()
slug: Web/API/BaseAudioContext/createWaveShaper
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createWaveShaper
---

{{ APIRef("Web Audio API") }}

متد `createWaveShaper()` از رابط {{ domxref("BaseAudioContext") }} یک {{ domxref("WaveShaperNode") }} ایجاد می‌کند که یک اعوجاج غیرخطی را نشان می‌دهد. از آن برای اعمال افکت‌های اعوجاج به صدای خود استفاده می‌شود.

> [!NOTE]
> سازنده {{domxref("WaveShaperNode.WaveShaperNode", "WaveShaperNode()")}}
> روش توصیه‌شده برای ایجاد یک {{domxref("WaveShaperNode")}} است؛ برای اطلاعات بیشتر به
> [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## نحو (Syntax)

```js-nolint
createWaveShaper()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{domxref("WaveShaperNode")}}.

## مثال‌ها

مثال زیر کاربرد پایه‌ای یک AudioContext را برای ایجاد یک گره شکل‌دهنده موج نشان می‌دهد.
برای مثال‌های کاربردی‌تر و اطلاعات کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط به [app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js) مراجعه کنید).

> [!NOTE]
> توابع سیگموئید معمولاً برای منحنی‌های اعوجاج استفاده می‌شوند
> به دلیل ویژگی‌های طبیعی‌شان. به عنوان مثال، شکل S آن‌ها به ایجاد نتیجه‌ای
> نرم‌تر کمک می‌کند. کد منحنی اعوجاج زیر را در [Stack Overflow](https://stackoverflow.com/questions/22312841/waveshaper-node-in-webaudio-how-to-emulate-distortion) پیدا کردیم.

```js
const audioCtx = new AudioContext();
const distortion = audioCtx.createWaveShaper();

// …

function makeDistortionCurve(amount) {
  const k = typeof amount === "number" ? amount : 50;
  const numSamples = 44100;
  const curve = new Float32Array(numSamples);
  const deg = Math.PI / 180;

  for (let i = 0; i < numSamples; i++) {
    const x = (i * 2) / numSamples - 1;
    curve[i] = ((3 + k) * x * 20 * deg) / (Math.PI + k * Math.abs(x));
  }
  return curve;
}

// …

distortion.curve = makeDistortionCurve(400);
distortion.oversample = "4x";
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)