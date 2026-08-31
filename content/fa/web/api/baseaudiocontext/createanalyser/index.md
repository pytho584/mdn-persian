---
title: "BaseAudioContext: createAnalyser() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createAnalyser"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createAnalyser() method"
short-title: createAnalyser()
slug: Web/API/BaseAudioContext/createAnalyser
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createAnalyser
---

{{APIRef("Web Audio API")}}

متد `createAnalyser()` از رابط {{domxref("BaseAudioContext")}} یک {{domxref("AnalyserNode")}} ایجاد می‌کند که می‌توان از آن برای نمایش داده‌های زمانی و فرکانسی صدا و ایجاد تجسم‌های داده استفاده کرد.

> [!NOTE]
> سازنده {{domxref("AnalyserNode.AnalyserNode", "AnalyserNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("AnalyserNode")}} است؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

> [!NOTE]
> برای اطلاعات بیشتر در مورد استفاده از این گره، به صفحه {{domxref("AnalyserNode")}} مراجعه کنید.

## Syntax

```js-nolint
createAnalyser()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{domxref("AnalyserNode")}}.

## مثال‌ها

مثال زیر کاربرد پایه‌ای یک AudioContext برای ایجاد یک گره Analyser و سپس استفاده از `requestAnimationFrame()` برای جمع‌آوری مکرر داده‌های حوزه زمانی و رسم خروجی "نوسان‌نما" از ورودی صوتی فعلی را نشان می‌دهد. برای مثال‌ها/اطلاعات کاربردی کامل‌تر، به دموی [Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) ما مراجعه کنید (کدهای مربوطه را در [app.js خطوط 108-193](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) ببینید).

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 2048;
const bufferLength = analyser.frequencyBinCount;
const dataArray = new Uint8Array(bufferLength);
analyser.getByteTimeDomainData(dataArray);

// رسم یک نوسان‌نما از منبع صوتی فعلی

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)