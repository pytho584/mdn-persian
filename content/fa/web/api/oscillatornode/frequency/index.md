---
title: "OscillatorNode: frequency property"
short-title: frequency
slug: Web/API/OscillatorNode/frequency
page-type: web-api-instance-property
browser-compat: api.OscillatorNode.frequency
---

{{ APIRef("Web Audio API") }}

ویژگی **`frequency`** در رابط {{ domxref("OscillatorNode") }} یک {{domxref("AudioParam")}} با [نرخ a](/en-US/docs/Web/API/AudioParam#a-rate) است که بسامد (فرکانس) نوسان را بر حسب هرتز نشان می‌دهد.

> [!NOTE]
> اگرچه شیء `AudioParam` بازگردانده‌شده فقط‌خواندنی است، مقداری که نشان می‌دهد قابل تغییر است.

## مقدار

یک {{domxref("AudioParam")}} با [نرخ a](/en-US/docs/Web/API/AudioParam#a-rate).

## مثال‌ها

مثال زیر کاربرد پایه‌ای {{ domxref("AudioContext") }} را برای ایجاد یک گره نوسان‌ساز نشان می‌دهد. برای یک مثال کاربردی، به [دموی Violent Theremin](https://mdn.github.io/webaudio-examples/violent-theremin/) مراجعه کنید ([کدهای مربوطه را در app.js](https://github.com/mdn/webaudio-examples/blob/main/violent-theremin/scripts/app.js) ببینید).

```js
// create web audio api context
const audioCtx = new AudioContext();

// create Oscillator node
const oscillator = audioCtx.createOscillator();

oscillator.type = "square";
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // value in hertz
oscillator.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)