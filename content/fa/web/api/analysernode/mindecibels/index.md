---
title: "AnalyserNode: minDecibels property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/minDecibels"
translated_by: "n8n + AI"
---

---
title: "AnalyserNode: minDecibels property"
short-title: minDecibels
slug: Web/API/AnalyserNode/minDecibels
page-type: web-api-instance-property
browser-compat: api.AnalyserNode.minDecibels
---

{{ APIRef("Web Audio API") }}

ویژگی **`minDecibels`** در رابط {{ domxref("AnalyserNode") }} یک مقدار اعشاری (double) است که حداقل مقدار توان را در محدوده‌ی مقیاس‌بندی برای داده‌های تحلیل FFT مشخص می‌کند، برای تبدیل به مقادیر بایت بدون علامت — به طور کلی، این ویژگی حداقل مقدار را برای محدوده‌ی نتایج هنگام استفاده از `getByteFrequencyData()` تعیین می‌کند.

## مقدار

یک double که حداقل مقدار [دسی‌بل](https://en.wikipedia.org/wiki/Decibel) را برای مقیاس‌بندی داده‌های تحلیل FFT نشان می‌دهد، جایی که `0` دسی‌بل بلندترین صدای ممکن است، `10-` دسی‌بل یک‌دهم آن است، و غیره. مقدار پیش‌فرض `100-` دسی‌بل است.

هنگام دریافت داده‌ها از `getByteFrequencyData()`، هر فرکانسی که دامنه‌ی آن `minDecibels` یا کمتر باشد، به صورت `0` بازگردانده می‌شود.

> [!NOTE]
> اگر مقدار بزرگتری نسبت به `AnalyserNode.maxDecibels` تنظیم شود، یک استثنای `INDEX_SIZE_ERR` پرتاب می‌شود.

## مثال‌ها

مثال زیر کاربرد اساسی {{domxref("AudioContext")}} برای ایجاد یک `AnalyserNode` و سپس {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} و {{htmlelement("canvas")}} برای جمع‌آوری مکرر داده‌های فرکانس و رسم خروجی به سبک "نمودار میله‌ای winamp" از ورودی صوتی فعلی را نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی‌تر و کامل‌تر، نمایش [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مربوطه به [خطوط ۱۰۸ تا ۱۹۳ فایل app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

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