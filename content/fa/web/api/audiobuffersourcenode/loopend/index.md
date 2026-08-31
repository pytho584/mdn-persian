---
title: "AudioBufferSourceNode: loopEnd property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/loopEnd"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: loopEnd property"
short-title: loopEnd
slug: Web/API/AudioBufferSourceNode/loopEnd
page-type: web-api-instance-property
browser-compat: api.AudioBufferSourceNode.loopEnd
---

{{ APIRef("Web Audio API") }}

ویژگی `loopEnd` از رابط {{ domxref("AudioBufferSourceNode") }} یک عدد اعشاری است که بر حسب ثانیه مشخص می‌کند در چه نقطه‌ای از پخش {{domxref("AudioBuffer")}}، پخش باید به زمانی که توسط ویژگی {{domxref("AudioBufferSourceNode.loopStart", "loopStart")}} مشخص شده است، بازگردد. این ویژگی تنها زمانی استفاده می‌شود که ویژگی {{domxref("AudioBufferSourceNode.loop", "loop")}} برابر با `true` باشد.

## مقدار

یک عدد اعشاری که نشان‌دهنده‌ی افست (بر حسب ثانیه) در بافر صوتی است که در آن هر حلقه به ابتدای حلقه بازمی‌گردد (یعنی زمان پخش فعلی به مقدار {{domxref("AudioBufferSourceNode.loopStart")}} بازنشانی می‌شود). این ویژگی تنها زمانی استفاده می‌شود که ویژگی {{domxref("AudioBufferSourceNode.loop", "loop")}} برابر با `true` باشد.

مقدار پیش‌فرض 0 است.

## مثال‌ها

### تنظیم `loopEnd`

در این مثال، هنگامی که کاربر دکمه‌ی "Play" را فشار می‌دهد، یک قطعه صوتی بارگذاری می‌شود، رمزگشایی می‌شود و در یک {{domxref("AudioBufferSourceNode")}} قرار می‌گیرد.

سپس مثال، ویژگی `loop` را روی `true` تنظیم می‌کند تا قطعه تکرار شود و قطعه را پخش می‌کند.

کاربر می‌تواند ویژگی‌های `loopStart` و `loopEnd` را با استفاده از [کنترل‌های محدوده](/en-US/docs/Web/HTML/Reference/Elements/input/range) تنظیم کند.

> [!NOTE]
> می‌توانید [مثال کامل را به صورت زنده اجرا کنید](https://mdn.github.io/webaudio-examples/audio-buffer-source-node/loop/) (یا [کد منبع را مشاهده کنید](https://github.com/mdn/webaudio-examples/tree/main/audio-buffer-source-node/loop)).

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)