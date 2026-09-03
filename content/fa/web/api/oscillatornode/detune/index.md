---
title: "OscillatorNode: detune property"
short-title: detune
slug: Web/API/OscillatorNode/detune
page-type: web-api-instance-property
browser-compat: api.OscillatorNode.detune
---

{{ APIRef("Web Audio API") }}

ویژگی `detune` از رابط {{ domxref("OscillatorNode") }} یک {{domxref("AudioParam")}} با نرخ-a ([a-rate](/en-US/docs/Web/API/AudioParam#a-rate)) است که میزان انحراف از کوک (detuning) نوسان را بر حسب [سنت](https://en.wikipedia.org/wiki/Cent_%28music%29) نشان می‌دهد.

> [!NOTE]
> اگرچه شیء `AudioParam` بازگردانده‌شده فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مقدار

یک {{domxref("AudioParam")}} با نرخ-a ([a-rate](/en-US/docs/Web/API/AudioParam#a-rate)).

## مثال‌ها

مثال زیر کاربرد پایه‌ای {{ domxref("AudioContext") }} را برای ساخت یک گره نوسان‌گر نشان می‌دهد. برای مثال‌ها و اطلاعات کاربردی، به [دموی Violent Theremin](https://mdn.github.io/webaudio-examples/violent-theremin/) مراجعه کنید ([کد مرتبط را در app.js](https://github.com/mdn/webaudio-examples/blob/main/violent-theremin/scripts/app.js) ببینید).

```js
// ایجاد context برای Web Audio API
const audioCtx = new AudioContext();

// ایجاد گره Oscillator
const oscillator = audioCtx.createOscillator();

oscillator.type = "square";
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // مقدار بر حسب هرتز
oscillator.detune.setValueAtTime(100, audioCtx.currentTime); // مقدار بر حسب سنت
oscillator.start();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)