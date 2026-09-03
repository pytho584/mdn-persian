---
title: "OscillatorNode: type property"
short-title: type
slug: Web/API/OscillatorNode/type
page-type: web-api-instance-property
browser-compat: api.OscillatorNode.type
---

{{ APIRef("Web Audio API") }}

ویژگی **`type`** از رابط {{domxref("OscillatorNode")}} مشخص می‌کند که نوسان‌ساز چه شکلی از [شکل موج](https://en.wikipedia.org/wiki/Waveform) را خروجی دهد. چندین شکل موج رایج در دسترس هستند، و همچنین گزینه‌ای برای تعیین یک شکل موج سفارشی وجود دارد. شکل موج بر تُن تولید شده تأثیر می‌گذارد.

## مقدار

یک رشته که شکل موج نوسان‌ساز را مشخص می‌کند. مقادیر مختلف موجود عبارتند از:

- `sine`
  - : یک [موج سینوسی](https://en.wikipedia.org/wiki/Sine_wave). این مقدار پیش‌فرض است.
- `square`
  - : یک [موج مربعی](https://en.wikipedia.org/wiki/Square_wave) با [چرخه وظیفه](https://en.wikipedia.org/wiki/Duty_cycle) 0.5؛ یعنی سیگنال به مدت نیمی از هر دوره «بالا» است.
- `sawtooth`
  - : یک [موج دندانه‌اره‌ای](https://en.wikipedia.org/wiki/Sawtooth_wave).
- `triangle`
  - : یک [موج مثلثی](https://en.wikipedia.org/wiki/Triangle_wave).
- `custom`
  - : یک شکل موج سفارشی. شما هرگز `type` را به صورت دستی روی `custom` تنظیم نمی‌کنید؛ بلکه از روش {{domxref("OscillatorNode.setPeriodicWave", "setPeriodicWave()")}} برای ارائه داده‌های نمایانگر شکل موج استفاده کنید. انجام این کار به‌طور خودکار `type` را روی `custom` تنظیم می‌کند.

همچنین [انواع مختلف گره نوسان‌ساز](/en-US/docs/Web/API/OscillatorNode#different_oscillator_node_types) را برای نمایش تصویری شکل‌های موج مختلف ببینید.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر مقدار `custom` مشخص شده باشد پرتاب می‌شود. برای تنظیم یک شکل موج سفارشی، کافی است {{domxref("OscillatorNode.setPeriodicWave", "setPeriodicWave()")}} را فراخوانی کنید. انجام این کار به‌طور خودکار نوع را برای شما تنظیم می‌کند.

## مثال‌ها

مثال زیر نحوه استفاده پایه از یک {{ domxref("AudioContext") }} برای ایجاد یک گره نوسان‌ساز را نشان می‌دهد. برای یک مثال کاربردی، [نمونه Violent Theremin](https://mdn.github.io/webaudio-examples/violent-theremin/) ما را بررسی کنید ([app.js](https://github.com/mdn/webaudio-examples/blob/main/violent-theremin/scripts/app.js) را برای کد مرتبط ببینید).

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)