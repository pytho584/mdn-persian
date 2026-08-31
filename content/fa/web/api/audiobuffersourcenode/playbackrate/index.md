---
title: "AudioBufferSourceNode: playbackRate property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/playbackRate"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: playbackRate property"
short-title: playbackRate
slug: Web/API/AudioBufferSourceNode/playbackRate
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.playbackRate
---

{{ APIRef("Web Audio API") }}

ویژگی **`playbackRate`** در interface {{ domxref("AudioBufferSourceNode") }} یک {{domxref("AudioParam")}} از نوع [k-rate](/en-US/docs/Web/API/AudioParam#k-rate) است که سرعت پخش فایل صوتی را تعیین می‌کند.

مقدار `1.0` نشان می‌دهد که صدا باید با همان سرعت نرخ نمونه‌برداری خود پخش شود، مقادیر کمتر از `1.0` باعث می‌شوند صدا کندتر پخش شود، در حالی که مقادیر بیشتر از `1.0` باعث می‌شوند صدا سریع‌تر از حالت عادی پخش شود. مقدار پیش‌فرض `1.0` است. وقتی به مقدار دیگری تنظیم شود، `AudioBufferSourceNode` صدا را قبل از ارسال به خروجی، دوباره نمونه‌برداری (resample) می‌کند.

## مقدار

یک {{domxref("AudioParam")}} که {{domxref("AudioParam.value", "value")}} آن یک عدد اعشاری است که نرخ پخش صدا را به صورت نسبت اعشاری از نرخ نمونه‌برداری اصلی نشان می‌دهد.

یک بافر صوتی را در نظر بگیرید که حاوی صدایی با نمونه‌برداری ۴۴.۱ کیلوهرتز (۴۴٬۱۰۰ نمونه در ثانیه) است. بیایید ببینیم چند مقدار مختلف `playbackRate` چه می‌کنند:

- `playbackRate` برابر با `1.0` صدا را با سرعت کامل پخش می‌کند، یعنی ۴۴٬۱۰۰ هرتز.
- `playbackRate` برابر با `0.5` صدا را با نصف سرعت پخش می‌کند، یعنی ۲۲٬۰۵۰ هرتز.
- `playbackRate` برابر با `2.0` نرخ پخش صدا را به ۸۸٬۲۰۰ هرتز دو برابر می‌کند.

## مثال‌ها

### تنظیم `playbackRate`

در این مثال، وقتی کاربر دکمه «Play» را فشار می‌دهد، ما یک فایل صوتی بارگذاری می‌کنیم، آن را decode می‌کنیم و در یک {{domxref("AudioBufferSourceNode")}} قرار می‌دهیم.

سپس مثال ویژگی `loop` را روی `true` تنظیم می‌کند تا حلقه تکرار شود و آهنگ پخش شود.

کاربر می‌تواند ویژگی `playbackRate` را با استفاده از یک [کنترل بازه‌ای (range control)](/en-US/docs/Web/HTML/Reference/Elements/input/range) تنظیم کند.

> [!NOTE]
> می‌توانید [مثال کامل را به صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer-source-node/playbackrate/) (یا [سورس کد را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/audio-buffer-source-node/playbackrate)).

```js
let audioCtx;
let buffer;
let source;

const play = document.getElementById("play");
const stop = document.getElementById("stop");

const playbackControl = document.getElementById("playback-rate-control");
const playbackValue = document.getElementById("playback-rate-value");

async function loadAudio() {
  try {
    // Load an audio file
    const response = await fetch("rnb-lofi-melody-loop.wav");
    // Decode it
    buffer = await audioCtx.decodeAudioData(await response.arrayBuffer());
  } catch (err) {
    console.error(`Unable to fetch the audio file. Error: ${err.message}`);
  }
}

play.addEventListener("click", async () => {
  if (!audioCtx) {
    audioCtx = new AudioContext();
    await loadAudio();
  }
  source = audioCtx.createBufferSource();
  source.buffer = buffer;
  source.connect(audioCtx.destination);
  source.loop = true;
  source.playbackRate.value = playbackControl.value;
  source.start();
  play.disabled = true;
  stop.disabled = false;
  playbackControl.disabled = false;
});

stop.addEventListener("click", () => {
  source.stop();
  play.disabled = false;
  stop.disabled = true;
  playbackControl.disabled = true;
});

playbackControl.oninput = () => {
  source.playbackRate.value = playbackControl.value;
  playbackValue.textContent = playbackControl.value;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)