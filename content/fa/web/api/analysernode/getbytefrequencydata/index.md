---
title: "AnalyserNode: getByteFrequencyData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/getByteFrequencyData"
translated_by: "n8n + AI"
---

 `getByteFrequencyData()`

متد `getByteFrequencyData()` رابط `AnalyserNode`، داده‌های فرکانسیِ لحظه‌ای را درون یک `Uint8Array` (آرایه‌ای از اعداد صحیح بدون علامت) که به آن پاس می‌دهید، کپی می‌کند.

این داده‌ها به صورت اعداد صحیحی بین ۰ تا ۲۵۵ هستند.

هر عضو آرایه، نشان‌دهندهٔ مقدار دسی‌بل (dB) یک فرکانس مشخص است. فرکانس‌ها به صورت خطی از ۰ تا نصف نرخ نمونه‌برداری (sample rate) توزیع شده‌اند. برای مثال، اگر نرخ نمونه‌برداری `48000` باشد، آخرین عضو آرایه مقدار دسی‌بل فرکانس `24000` هرتز را نشان می‌دهد.

اگر آرایه‌ای که پاس می‌دهید عناصر کمتری نسبت به `AnalyserNode.frequencyBinCount` داشته باشد، عناصر اضافی حذف می‌شوند. اگر عناصر بیشتری داشته باشد، عناصر اضافی نادیده گرفته می‌شوند.

## Syntax

```js-nolint
getByteFrequencyData(array)
```

### Parameters

- `array`
  - : `Uint8Array`ای که داده‌های حوزهٔ فرکانس (frequency domain) در آن کپی می‌شود.
    اگر این آرایه عناصر کمتری نسبت به `AnalyserNode.frequencyBinCount` داشته باشد، عناصر اضافی حذف می‌شوند و اگر عناصر بیشتری داشته باشد، عناصر اضافی نادیده گرفته می‌شوند.

### Return value

هیچ چیز (`undefined`).

## Examples

مثال زیر نحوهٔ استفادهٔ پایه از `AudioContext` برای ساخت یک `AnalyserNode` و سپس بهره‌گیری از `requestAnimationFrame` و `<canvas>` را نشان می‌دهد؛ به این صورت که داده‌های فرکانسی به طور مکرر جمع‌آوری شده و خروجی به سبک نمودار میله‌ای «وینمپ» (Winamp) برای ورودی صدای جاری رسم می‌شود. برای مثال‌های کاربردی کامل‌تر، دمو [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) را ببینید (کد مربوطه در [app.js خطوط ۱۰۸ تا ۱۹۳](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) قرار دارد).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 256;
const bufferLength = analyser.frequencyBinCount;
console.log(bufferLength);
const dataArray = new Uint8Array(bufferLength);

canvasCtx.clearRect(0, 0, WIDTH, HEIGHT);

function draw() {
  drawVisual = requestAnimationFrame(draw);

  analyser.getByteFrequencyData(dataArray);

  canvasCtx.fillStyle = "rgb(0 0 0)";
  canvasCtx.fillRect(0, 0, WIDTH, HEIGHT);

  const barWidth = (WIDTH / bufferLength) * 2.5;
  let barHeight;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    barHeight = dataArray[i];

    canvasCtx.fillStyle = `rgb(${barHeight + 100} 50 50)`;
    canvasCtx.fillRect(x, HEIGHT - barHeight / 2, barWidth, barHeight / 2);

    x += barWidth + 1;
  }
}

draw();
```

## Specifications

## Browser compatibility

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)