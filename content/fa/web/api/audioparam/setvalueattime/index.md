---
title: "AudioParam: setValueAtTime() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/setValueAtTime"
translated_by: "n8n + AI"
---

---
title: "AudioParam: setValueAtTime() method"
short-title: setValueAtTime()
slug: Web/API/AudioParam/setValueAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.setValueAtTime
---

{{ APIRef("Web Audio API") }}

متد `setValueAtTime()` از رابط {{domxref("AudioParam")}} یک تغییر فوری در مقدار `AudioParam` را در زمان دقیقی، که بر اساس {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} اندازه‌گیری می‌شود، زمان‌بندی می‌کند. مقدار جدید در پارامتر value داده می‌شود.

## نحو (Syntax)

```js-nolint
setValueAtTime(value, startTime)
```

### پارامترها

- `value`
  - : یک عدد اعشاری (floating point) که نشان‌دهنده مقداری است که AudioParam در زمان مشخص‌شده به آن تغییر خواهد کرد.
- `startTime`
  - : یک عدد double که نشان‌دهنده زمان (به ثانیه) پس از ایجاد اولین بار {{domxref("AudioContext")}} است که تغییر مقدار در آن رخ می‌دهد. اگر این زمان کمتر از {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} باشد، تغییر بلافاصله اتفاق می‌افتد. اگر این مقدار منفی باشد، یک {{jsxref("TypeError")}} پرتاب می‌شود.

### مقدار بازگشتی

یک ارجاع به این شیء `AudioParam`. در برخی مرورگرها، پیاده‌سازی‌های قدیمی‌تر این رابط {{jsxref('undefined')}} را برمی‌گردانند.

## مثال‌ها

این مثال ساده شامل یک منبع رسانه‌ای (media element) با دو دکمه کنترل است (کد منبع را در [مخزن webaudio-examples](https://github.com/mdn/webaudio-examples/blob/main/audio-param/index.html) ببینید، یا [مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/webaudio-examples/audio-param/)). وقتی دکمه‌ها فشرده می‌شوند، متغیر `currGain` به مقدار 0.25 افزایش/کاهش می‌یابد، سپس از متد `setValueAtTime()` برای تنظیم مقدار gain برابر با `currGain`، یک ثانیه بعد از حالا (`audioCtx.currentTime + 1`) استفاده می‌شود.

```js
// create audio context
const audioCtx = new AudioContext();

// set basic variables for example
const myAudio = document.querySelector("audio");
const pre = document.querySelector("pre");
const myScript = document.querySelector("script");

pre.textContent = myScript.textContent;

const targetAtTimePlus = document.querySelector(".set-target-at-time-plus");
const targetAtTimeMinus = document.querySelector(".set-target-at-time-minus");

// Create a MediaElementAudioSourceNode
// Feed the HTMLMediaElement into it
const source = audioCtx.createMediaElementSource(myAudio);

// Create a gain node and set its gain value to 0.5
const gainNode = audioCtx.createGain();
gainNode.gain.value = 0.5;
let currGain = gainNode.gain.value;

// connect the AudioBufferSourceNode to the gainNode
// and the gainNode to the destination
source.connect(gainNode);
gainNode.connect(audioCtx.destination);

// set buttons to do something onclick
targetAtTimePlus.onclick = () => {
  currGain += 0.25;
  gainNode.gain.setValueAtTime(currGain, audioCtx.currentTime + 1);
};

targetAtTimeMinus.onclick = () => {
  currGain -= 0.25;
  gainNode.gain.setValueAtTime(currGain, audioCtx.currentTime + 1);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)