```markdown
---
title: "PeriodicWave: PeriodicWave() constructor"
short-title: PeriodicWave()
slug: Web/API/PeriodicWave/PeriodicWave
page-type: web-api-constructor
browser-compat: api.PeriodicWave.PeriodicWave
---

{{APIRef("Web Audio API")}}

سازنده `PeriodicWave()` از رابط برنامه‌نویسی Web Audio API یک نمونه جدید از شیء {{domxref("PeriodicWave")}} ایجاد می‌کند.

## Syntax

```js-nolint
new PeriodicWave(context)
new PeriodicWave(context, options)
```

### Parameters

- `context`
  - : یک {{domxref("BaseAudioContext")}} که زمینه صوتی مورد نظر برای ارتباط گره را نشان می‌دهد.
- `options` {{optional_inline}}
  - : یک شیء دیکشنری [`PeriodicWaveOptions`](https://webaudio.github.io/web-audio-api/#idl-def-PeriodicWaveOptions) که ویژگی‌های مورد نظر برای `PeriodicWave` را تعریف می‌کند (این شیء همچنین گزینه‌های تعریف‌شده در دیکشنری [PeriodicWaveConstraints](https://webaudio.github.io/web-audio-api/#idl-def-PeriodicWaveConstraints) را به ارث می‌برد):
    - `real`
      - : یک {{jsxref("Float32Array")}} شامل عبارت‌های کسینوسی که برای تشکیل موج استفاده می‌شوند (معادل پارامتر `real` در {{domxref("BaseAudioContext.createPeriodicWave")}}).
    - `imag`
      - : یک {{jsxref("Float32Array")}} شامل عبارت‌های سینوسی که برای تشکیل موج استفاده می‌شوند (معادل پارامتر `imag` در {{domxref("BaseAudioContext.createPeriodicWave")}}).
    - `channelCount`
      - : یک عدد صحیح که مشخص می‌کند هنگام [up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به ورودی‌های گره از چند کانال استفاده شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی که معنای کانال‌ها را توصیف می‌کند. این تفسیر مشخص می‌کند که [up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا چگونه انجام شود. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### Return value

یک نمونه جدید از شیء {{domxref("PeriodicWave")}}.

## نمونه‌ها

```js
const real = new Float32Array(2);
const imag = new Float32Array(2);
const ac = new AudioContext();

real[0] = 0;
imag[0] = 0;
real[1] = 1;
imag[1] = 0;

const wave = new PeriodicWave(ac, {
  real,
  imag,
  disableNormalization: false,
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
```