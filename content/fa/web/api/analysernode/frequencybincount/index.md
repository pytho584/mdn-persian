---
title: "AnalyserNode: frequencyBinCount property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/frequencyBinCount"
translated_by: "n8n + AI"
---

ویژگی `frequencyBinCount` در `AnalyserNode`
=============================================

ویژگی فقط‌خواندنی `frequencyBinCount` در اینترفیس `AnalyserNode`، تعداد کل نقاط داده‌ای را که با توجه به نرخ نمونه‌برداری `AudioContext` ([`sampleRate`](/en-US/docs/Web/API/BaseAudioContext/sampleRate)) در دسترس هستند، نشان می‌دهد. این مقدار نصف `fftSize` در `AnalyserNode` است. شاخص‌های آرایۀ خروجی دو متد `getByteFrequencyData` و `getFloatFrequencyData` رابطۀ خطی با فرکانس‌های متناظر دارند، از ۰ تا [فرکانس نایکوئیست](https://en.wikipedia.org/wiki/Nyquist_frequency).

مقدار
-----

یک عدد صحیح بدون علامت (unsigned integer) برابر با تعداد مقادیری که متدهای [`getByteFrequencyData()`](/en-US/docs/Web/API/AnalyserNode/getByteFrequencyData) و [`getFloatFrequencyData()`](/en-US/docs/Web/API/AnalyserNode/getFloatFrequencyData) در آرایۀ `TypedArray` ارائه‌شده کپی می‌کنند.

به دلایل فنی مربوط به نحوۀ تعریف تبدیل فوریۀ سریع (FFT)، این مقدار همواره نصف مقدار [`fftSize`](/en-US/docs/Web/API/AnalyserNode/fftSize) است. بنابراین، یکی از مقادیر `16`، `32`، `64`، `128`، `256`، `512`، `1024`، `2048`، `4096`، `8192` و `16384` خواهد بود.

مثال‌ها
--------

مثال زیر کاربرد پایه‌ای از یک `AudioContext` را برای ایجاد یک `AnalyserNode` نشان می‌دهد، سپس از [`requestAnimationFrame`](/en-US/docs/Web/API/Window/requestAnimationFrame) و عنصر [`<canvas>`](/en-US/docs/Web/HTML/Element/canvas) برای جمع‌آوری مکرر داده‌های فرکانسی و رسم خروجی «نمودار میله‌ای به سبک وینامپ» از ورودی صوتی فعلی استفاده می‌کند.  
برای نمونه‌های کاربردی کامل‌تر و اطلاعات بیشتر، دموی [Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) ما را ببینید.

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

  const barWidth = (WIDTH / bufferLength) * 2.5 - 1;
  let barHeight;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    barHeight = dataArray[i];

    canvasCtx.fillStyle = `rgb(${barHeight + 100} 50 50)`;
    canvasCtx.fillRect(x, HEIGHT - barHeight / 2, barWidth, barHeight / 2);

    x += barWidth;
  }
}

draw();
```

مشخصات
--------

سازگاری مرورگرها
-----------------

همچنین ببینید
--------------

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)