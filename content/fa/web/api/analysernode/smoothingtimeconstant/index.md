---
title: "AnalyserNode: smoothingTimeConstant property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/smoothingTimeConstant"
translated_by: "n8n + AI"
---

---
title: "AnalyserNode: smoothingTimeConstant property"
short-title: smoothingTimeConstant
slug: Web/API/AnalyserNode/smoothingTimeConstant
page-type: web-api-instance-property
browser-compat: api.AnalyserNode.smoothingTimeConstant
---

{{ APIRef("Web Audio API") }}

ویژگی **`smoothingTimeConstant`** از رابط {{ domxref("AnalyserNode") }} یک مقدار اعشاری است که ثابت میانگین‌گیری با آخرین فریم تحلیل را نشان می‌دهد. این مقدار اساساً میانگینی بین بافر کنونی و آخرین بافری است که `AnalyserNode` پردازش کرده است و منجر به مجموعه‌ای بسیار نرم‌تر از تغییرات مقدار در طول زمان می‌شود.

## مقدار

یک عدد اعشاری در بازه `0` تا `1` (مقدار `0` به معنای عدم میانگین‌گیری زمانی). مقدار پیش‌فرض `0.8` است.

اگر مقدار `0` تنظیم شود، هیچ میانگین‌گیری انجام نمی‌شود، در حالی که مقدار `1` به معنای «هم‌پوشانی قابل توجه بافر قبلی و فعلی هنگام محاسبه مقدار» است که اساساً تغییرات را در فراخوانی‌های {{domxref("AnalyserNode.getFloatFrequencyData")}}/{{domxref("AnalyserNode.getByteFrequencyData")}} نرم می‌کند.

از نظر فنی، ما یک [پنجره بلکمن](https://webaudio.github.io/web-audio-api/#blackman-window) اعمال کرده و مقادیر را در طول زمان نرم می‌کنیم. مقدار پیش‌فرض برای بیشتر موارد کافی است.

> [!NOTE]
> اگر مقداری خارج از بازه 0–1 تنظیم شود، یک استثنای `INDEX_SIZE_ERR` پرتاب می‌شود.

## مثال‌ها

مثال زیر کاربرد پایه‌ای یک {{domxref("AudioContext")}} برای ایجاد یک `AnalyserNode` و سپس استفاده از {{domxref("window.requestAnimationFrame()","requestAnimationFrame")}} و {{htmlelement("canvas")}} برای جمع‌آوری مکرر داده‌های فرکانس و رسم خروجی «نوار نمودار سبک winamp» از ورودی صوتی جاری را نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را بررسی کنید (برای کد مرتبط به [خطوط 108–193 app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

اگر در مورد تأثیر `smoothingTimeConstant()` کنجکاو هستید، سعی کنید مثال بالا را کلون کرده و `analyser.smoothingTimeConstant = 0;` را تنظیم کنید. متوجه خواهید شد که تغییرات مقدار بسیار ناهموارتر هستند.

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();
analyser.minDecibels = -90;
analyser.maxDecibels = -10;
analyser.smoothingTimeConstant = 0.85;

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

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)