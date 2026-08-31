---
title: "AnalyserNode: maxDecibels property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/maxDecibels"
translated_by: "n8n + AI"
---

---
title: "AnalyserNode: maxDecibels property"
short-title: maxDecibels
slug: Web/API/AnalyserNode/maxDecibels
page-type: web-api-instance-property
browser-compat: api.AnalyserNode.maxDecibels
---

{{APIRef("Web Audio API")}}

ویژگی **`maxDecibels`** از رابط {{domxref("AnalyserNode")}} یک مقدار double است که حداکثر مقدار توان را در محدوده مقیاس‌بندی داده‌های تحلیل FFT، برای تبدیل به مقادیر بایت بدون علامت، نشان می‌دهد — به عبارت ساده، این حداکثر مقدار برای محدوده نتایج هنگام استفاده از `getByteFrequencyData()` را مشخص می‌کند.

## مقدار

یک double، که حداکثر مقدار [دسیبل](https://en.wikipedia.org/wiki/Decibel) را برای مقیاس‌بندی داده‌های تحلیل FFT نشان می‌دهد، جایی که `0` dB بلندترین صدای ممکن است، `10-` dB یک‌دهم آن است و غیره. مقدار پیش‌فرض `30-` dB است.

هنگام دریافت داده‌ها از `getByteFrequencyData()`، هر فرکانسی با دامنه `maxDecibels` یا بالاتر به صورت `255` برگردانده می‌شود.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر مقداری کمتر یا مساوی با `AnalyserNode.minDecibels` تنظیم شود، پرتاب می‌شود.

## مثال‌ها

مثال زیر کاربرد پایه‌ای از یک {{domxref("AudioContext")}} برای ایجاد یک `AnalyserNode`، سپس {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} و {{htmlelement("canvas")}} برای جمع‌آوری مکرر داده‌های فرکانس و رسم خروجی «سبک نمودار میله‌ای winamp» از ورودی صوتی فعلی را نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کدهای مرتبط، [خطوط ۱۰۸–۱۹۳ app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) را مشاهده کنید).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();
analyser.minDecibels = -90;
analyser.maxDecibels = -10;

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)