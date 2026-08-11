---
title: "AnalyserNode: getFloatFrequencyData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/getFloatFrequencyData"
translated_by: "n8n + AI"
---

 متد `getFloatFrequencyData()` از اینترفیس `AnalyserNode`، داده‌های فرکانسی فعلی را درون آرایهٔ `Float32Array`ای که به آن پاس داده شده، کپی می‌کند.

هر عضو این آرایه نشان‌دهندهٔ مقدار دسی‌بل (decibel) برای یک فرکانس مشخص است. فرکانس‌ها به صورت خطی از ۰ تا نصف نرخ نمونه‌برداری (sample rate) گسترده شده‌اند. مثلاً در نرخ نمونه‌برداری `48000` هرتز، آخرین عضو آرایه مقدار دسی‌بل برای فرکانس `24000` هرتز را نشان می‌دهد.

اگر به کارایی (performance) بیشتری نیاز دارید و دقت برایتان اهمیتی ندارد، می‌توانید به جای آن از `AnalyserNode.getByteFrequencyData()` استفاده کنید که روی `Uint8Array` کار می‌کند.

## Syntax

```js-nolint
getFloatFrequencyData(array)
```

### Parameters

- `array`
  - : آرایهٔ `Float32Array` که داده‌های حوزهٔ فرکانس (frequency domain) در آن کپی می‌شود. برای هر نمونهٔ (sample) بی‌صدا، مقدار `-Infinity` خواهد بود.
    اگر آرایه تعداد عضو کمتری نسبت به `AnalyserNode.frequencyBinCount` داشته باشد، اعضای اضافی حذف می‌شوند. اگر هم تعداد عضو بیشتری داشته باشد، اعضای اضافی نادیده گرفته می‌شوند.

### Return value

هیچ‌چیز (`undefined`).

## Examples

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();
// Float32Array should be the same length as the frequencyBinCount
const myDataArray = new Float32Array(analyser.frequencyBinCount);
// fill the Float32Array with data returned from getFloatFrequencyData()
analyser.getFloatFrequencyData(myDataArray);
```

### Drawing a spectrum

مثال زیر نحوهٔ استفادهٔ پایه از `AudioContext` را نشان می‌دهد تا یک `MediaElementAudioSourceNode` را به `AnalyserNode` وصل کنیم. در حالی که صدا در حال پخش است، با `requestAnimationFrame()` داده‌های فرکانسی را مرتب جمع‌آوری می‌کنیم و یک نمودار میله‌ای به سبک Winamp را روی عنصر `<canvas>` رسم می‌کنیم.

برای نمونه‌ها و اطلاعات کاربردی کامل‌تر، دمو [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) را ببینید (کدهای مرتبط در [خطوط ۱۰۸ تا ۱۹۳ app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) قرار دارند).

```js
const audioCtx = new AudioContext();

// Create audio source
// Here, we use an audio file, but this could also be e.g. microphone input
const audioEle = new Audio();
audioEle.src = "my-audio.mp3"; // Insert file name here
audioEle.autoplay = true;
audioEle.preload = "auto";
const audioSourceNode = audioCtx.createMediaElementSource(audioEle);

// Create analyser node
const analyserNode = audioCtx.createAnalyser();
analyserNode.fftSize = 256;
const bufferLength = analyserNode.frequencyBinCount;
const dataArray = new Float32Array(bufferLength);

// Set up audio node network
audioSourceNode.connect(analyserNode);
analyserNode.connect(audioCtx.destination);

// Create 2D canvas
const canvas = document.createElement("canvas");
canvas.style.position = "absolute";
canvas.style.top = "0";
canvas.style.left = "0";
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
document.body.appendChild(canvas);
const canvasCtx = canvas.getContext("2d");
canvasCtx.clearRect(0, 0, canvas.width, canvas.height);

function draw() {
  // Schedule next redraw
  requestAnimationFrame(draw);

  // Get spectrum data
  analyserNode.getFloatFrequencyData(dataArray);

  // Draw black background
  canvasCtx.fillStyle = "rgb(0 0 0)";
  canvasCtx.fillRect(0, 0, canvas.width, canvas.height);

 ```js
  // Draw spectrum
  const barWidth = (canvas.width / bufferLength) * 2.5;
  let posX = 0;
  for (let i = 0; i < bufferLength; i++) {
    const barHeight = (dataArray[i] + 140) * 2;
    canvasCtx.fillStyle = `rgb(${Math.floor(barHeight + 100)} 50 50)`;
    canvasCtx.fillRect(
      posX,
      canvas.height - barHeight / 2,
      barWidth,
      barHeight / 2,
    );
    posX += barWidth + 1;
  }
}

draw();
```

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
```