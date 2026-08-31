---
title: "AudioBufferSourceNode: loopStart property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/loopStart"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: loopStart property"
short-title: loopStart
slug: Web/API/AudioBufferSourceNode/loopStart
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.loopStart
---

{{ APIRef("Web Audio API") }}

ویژگی **`loopStart`** از رابط {{domxref("AudioBufferSourceNode")}} یک مقدار ممیز شناور است که بر حسب ثانیه تعیین می‌کند که در کجای {{domxref("AudioBuffer")}} باید پخش دوباره آغاز شود.

مقدار پیش‌فرض ویژگی `loopStart` برابر با `0` است.

## مقدار

یک عدد ممیز شناور که انحراف (offset) را بر حسب ثانیه درون بافر صوتی نشان می‌دهد؛ جایی که هر تکرار باید هنگام پخش از آنجا شروع شود. این مقدار تنها زمانی استفاده می‌شود که پارامتر {{domxref("AudioBufferSourceNode.loop", "loop")}} برابر با `true` باشد.

## مثال‌ها

### تنظیم `loopStart`

در این مثال، وقتی کاربر دکمهٔ «Play» را فشار می‌دهد، یک قطعهٔ صوتی بارگذاری می‌کنیم، آن را کدگشایی (decode) می‌کنیم و در یک {{domxref("AudioBufferSourceNode")}} قرار می‌دهیم.

سپس مثال، ویژگی `loop` را روی `true` تنظیم می‌کند تا قطعه به‌صورت حلقه درآید و آن را پخش کند.

کاربر می‌تواند ویژگی‌های `loopStart` و `loopEnd` را با استفاده از [کنترل‌های بازه](/en-US/docs/Web/HTML/Reference/Elements/input/range) تنظیم کند.

> [!NOTE]
> می‌توانید [نمونهٔ کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer-source-node/loop/) (یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/audio-buffer-source-node/loop).)

```js
let audioCtx;
let buffer;
let source;

const play = document.getElementById("play");
const stop = document.getElementById("stop");

const loopstartControl = document.getElementById("loopstart-control");
const loopstartValue = document.getElementById("loopstart-value");

const loopendControl = document.getElementById("loopend-control");
const loopendValue = document.getElementById("loopend-value");

async function loadAudio() {
  try {
    // Load an audio file
    const response = await fetch("rnb-lofi-melody-loop.wav");
    // Decode it
    buffer = await audioCtx.decodeAudioData(await response.arrayBuffer());
    const max = Math.floor(buffer.duration);
    loopstartControl.setAttribute("max", max);
    loopendControl.setAttribute("max", max);
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
  source.loopStart = loopstartControl.value;
  source.loopEnd = loopendControl.value;
  source.start();
  play.disabled = true;
  stop.disabled = false;
  loopstartControl.disabled = false;
  loopendControl.disabled = false;
});

stop.addEventListener("click", () => {
  source.stop();
  play.disabled = false;
  stop.disabled = true;
  loopstartControl.disabled = true;
  loopendControl.disabled = true;
});

loopstartControl.addEventListener("input", () => {
  source.loopStart = loopstartControl.value;
  loopstartValue.textContent = loopstartControl.value;
});

loopendControl.addEventListener("input", () => {
  source.loopEnd = loopendControl.value;
  loopendValue.textContent = loopendControl.value;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)