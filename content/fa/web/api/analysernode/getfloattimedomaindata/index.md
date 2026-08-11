---
title: "AnalyserNode: getFloatTimeDomainData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/getFloatTimeDomainData"
translated_by: "n8n + AI"
---

 ```markdown
## Syntax

```js-nolint
getFloatTimeDomainData(array)
```

### Parameters

- `array`
  - : آرایهٔ `Float32Array` که دادهٔ حوزهٔ زمان (time-domain) در آن کپی می‌شود.
    اگر اندازهٔ این آرایه از `AnalyserNode.fftSize` کوچک‌تر باشد، مقادیر اضافی (از سمت منبع) حذف می‌شوند؛ اگر بزرگ‌تر باشد، عناصر اضافی آن نادیده گرفته می‌شوند.

### Return value

هیچ (`undefined`).

## Examples

مثال زیر نحوهٔ استفادهٔ اولیه از `AudioContext` برای ساخت یک `AnalyserNode` را نشان می‌دهد؛ سپس با `requestAnimationFrame` و `<canvas>` دادهٔ حوزهٔ زمان را به‌طور مکرر جمع‌آوری کرده و خروجی را به سبک «نوسان‌نگار» (oscilloscope) برای ورودی صوتی فعلی رسم می‌کند.
برای نمونه‌های کاربردی کامل‌تر، نگاهی به دمو [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) بیندازید (کدهای مرتبط را در [app.js خطوط ۱۰۸ تا ۱۹۳](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) ببینید).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 1024;
const bufferLength = analyser.fftSize;
console.log(bufferLength);
const dataArray = new Float32Array(bufferLength);

canvasCtx.clearRect(0, 0, WIDTH, HEIGHT);

function draw() {
  drawVisual = requestAnimationFrame(draw);
  analyser.getFloatTimeDomainData(dataArray);

  canvasCtx.fillStyle = "rgb(200 200 200)";
  canvasCtx.fillRect(0, 0, WIDTH, HEIGHT);
  canvasCtx.lineWidth = 2;
  canvasCtx.strokeStyle = "rgb(0 0 0)";
  canvasCtx.beginPath();

  const sliceWidth = (WIDTH * 1.0) / bufferLength;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] * 200.0;
    const y = HEIGHT / 2 + v;

    if (i === 0) {
      canvasCtx.moveTo(x, y);
    } else {
      canvasCtx.lineTo(x, y);
    }
    x += sliceWidth;
  }

  canvasCtx.lineTo(canvas.width, canvas.height / 2);
  canvasCtx.stroke();
}

draw();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
```
```markdown
متد **`getFloatTimeDomainData()`** از رابط `AnalyserNode`، دادهٔ موج فعلی — یا همان دادهٔ حوزهٔ زمان (time-domain) — را در آرایهٔ `Float32Array`ای که به آن پاس می‌دهید، کپی می‌کند. هر مقدار در این آرایه یک نمونه (sample) است؛ یعنی اندازهٔ سیگنال در یک لحظهٔ زمانی مشخص.

این موج به صورت دادهٔ PCM نمایش داده می‌شود که محدودهٔ استاندارد آن از ۱٫۰- تا ۱٫۰ است، اگرچه مقادیر ممکن است از این بازه فراتر روند؛ مثلاً هنگام down-mixing کردن صدای استریو به مونو.

## Syntax

```js-nolint
getFloatTimeDomainData(array)
```

### Parameters

- `array`
  - : آرایهٔ `Float32Array` که دادهٔ حوزهٔ زمان (time-domain) در آن کپی می‌شود.
    اگر اندازهٔ این آرایه از `AnalyserNode.fftSize` کوچک‌تر باشد، مقادیر اضافی (از سمت منبع) حذف می‌شوند؛ اگر بزرگ‌تر باشد، عناصر اضافی آن نادیده گرفته می‌شوند.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

مثال زیر نحوهٔ استفادهٔ اولیه از `AudioContext` برای ساخت یک `AnalyserNode` را نشان می‌دهد؛ سپس با `requestAnimationFrame` و `<canvas>` دادهٔ حوزهٔ زمان را به‌طور مکرر جمع‌آوری کرده و خروجی را به سبک «نوسان‌نگار» (oscilloscope) برای ورودی صوتی فعلی رسم می‌کند.
برای نمونه‌های کاربردی کامل‌تر، نگاهی به دمو [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) بیندازید (کدهای مرتبط را در [app.js خطوط 108 تا 193](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) ببینید).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 1024;
const bufferLength = analyser.fftSize;
console.log(bufferLength);
const dataArray = new Float32Array(bufferLength);

canvasCtx.clearRect(0, 0, WIDTH, HEIGHT);

function draw() {
  drawVisual = requestAnimationFrame(draw);
  analyser.getFloatTimeDomainData(dataArray);

  canvasCtx.fillStyle = "rgb(200 200 200)";
  canvasCtx.fillRect(0, 0, WIDTH, HEIGHT);
  canvasCtx.lineWidth = 2;
  canvasCtx.strokeStyle = "rgb(0 0 0)";
  canvasCtx.beginPath();

  const sliceWidth = (WIDTH * 1.0) / bufferLength;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] * 200.0;
    const y = HEIGHT / 2 + v;

    if (i === 0) {
      canvasCtx.moveTo(x, y);
    } else {
      canvasCtx.lineTo(x, y);
   