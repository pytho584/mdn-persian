---
title: "AudioBufferSourceNode: loop property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/loop"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: loop property"
short-title: loop
slug: Web/API/AudioBufferSourceNode/loop
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.loop
---

{{ APIRef("Web Audio API") }}

ویژگی `loop` در رابط {{ domxref("AudioBufferSourceNode") }} یک مقدار بولی است که نشان می‌دهد آیا باید منبع صوتی هنگام رسیدن به انتهای {{domxref("AudioBuffer")}} دوباره پخش شود یا خیر.

مقدار پیش‌فرض ویژگی `loop` برابر با `false` است.

## مقدار

یک مقدار بولی که اگر حلقه فعال باشد `true` است؛ در غیر این صورت، مقدار آن `false` است.

وقتی حلقه فعال باشد، صدا از زمان مشخص‌شده به عنوان نقطه شروع هنگام فراخوانی {{domxref("AudioBufferSourceNode.start", "start()")}} پخش می‌شود. وقتی به زمان مشخص‌شده توسط ویژگی {{domxref("AudioBufferSourceNode.loopEnd", "loopEnd")}} برسیم، پخش از زمان مشخص‌شده توسط {{domxref("AudioBufferSourceNode.loopStart", "loopStart")}} ادامه می‌یابد.

## مثال‌ها

### تنظیم `loop`

در این مثال، وقتی کاربر دکمه «پخش» را فشار می‌دهد، یک فایل صوتی بارگیری می‌شود، رمزگشایی می‌شود و در یک {{domxref("AudioBufferSourceNode")}} قرار می‌گیرد.

سپس مثال ویژگی `loop` را روی `true` تنظیم می‌کند تا حلقه فعال شود و فایل پخش شود.

کاربر می‌تواند ویژگی‌های `loopStart` و `loopEnd` را با استفاده از [کنترل‌های بازه](/en-US/docs/Web/HTML/Reference/Elements/input/range) تنظیم کند.

> [!NOTE]
> می‌توانید [مثال کامل را به‌صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer-source-node/loop/) (یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/audio-buffer-source-node/loop).)

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
- {{domxref("AudioBufferSourceNode")}}