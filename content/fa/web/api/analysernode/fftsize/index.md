---
title: "AnalyserNode: fftSize property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/fftSize"
translated_by: "n8n + AI"
---

## ویژگی `fftSize`

ویژگی **`fftSize`** از واسط `AnalyserNode` یک مقدار عددی صحیح بدون علامت (unsigned long) است که اندازهٔ پنجره را بر حسب نمونه (sample) مشخص می‌کند. این اندازه هنگام اجرای [تبدیل فوریه سریع](https://en.wikipedia.org/wiki/Fast_Fourier_transform) (FFT) برای به‌دست آوردن داده‌های دامنهٔ فرکانس استفاده می‌شود.

## مقدار

یک عدد صحیح بدون علامت که اندازهٔ پنجرهٔ FFT را بر حسب تعداد نمونه نشان می‌دهد. هرچه مقدار بزرگ‌تر باشد، جزئیات بیشتری در دامنهٔ فرکانس و جزئیات کمتری در دامنهٔ دامنه (amplitude) خواهید داشت.

باید توانی از ۲ بین 2^5 و 2^15 باشد، یعنی یکی از مقادیر: `32`، `64`، `128`، `256`، `512`، `1024`، `2048`، `4096`، `8192`، `16384` و `32768`. مقدار پیش‌فرض `2048` است.

### استثناها

- `IndexSizeError` `DOMException`
  - : در صورتی که مقدار تنظیم‌شده توانی از ۲ نباشد یا خارج از بازهٔ مجاز قرار گیرد، صادر می‌شود.

## مثال‌ها

مثال زیر نحوهٔ استفادهٔ پایه‌ای از `AudioContext` برای ایجاد یک `AnalyserNode` و سپس استفاده از `requestAnimationFrame` و `<canvas>` را نشان می‌دهد تا داده‌های دامنهٔ زمان به‌طور مکرر جمع‌آوری شده و خروجی به سبک اسیلوسکوپ از ورودی صوتی جاری رسم شود.  
برای نمونه‌های کاربردی کامل‌تر و اطلاعات بیش‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (کد مربوط را در فایل `app.js`، خطوط ۱۰۸ تا ۱۹۳ دنبال کنید).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 2048;
const bufferLength = analyser.frequencyBinCount;
const dataArray = new Uint8Array(bufferLength);
analyser.getByteTimeDomainData(dataArray);

// draw an oscilloscope of the current audio source

function draw() {
  drawVisual = requestAnimationFrame(draw);

  analyser.getByteTimeDomainData(dataArray);

  canvasCtx.fillStyle = "rgb(200 200 200)";
  canvasCtx.fillRect(0, 0, WIDTH, HEIGHT);

  canvasCtx.lineWidth = 2;
  canvasCtx.strokeStyle = "rgb(0 0 0)";

  canvasCtx.beginPath();

  const sliceWidth = (WIDTH * 1.0) / bufferLength;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] / 128.0;
    const y = (v * HEIGHT) / 2;

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

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)