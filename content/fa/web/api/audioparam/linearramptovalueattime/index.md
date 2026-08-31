---
title: "AudioParam: linearRampToValueAtTime() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/linearRampToValueAtTime"
translated_by: "n8n + AI"
---

---
title: "AudioParam: linearRampToValueAtTime() method"
short-title: linearRampToValueAtTime()
slug: Web/API/AudioParam/linearRampToValueAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.linearRampToValueAtTime
---

{{ APIRef("Web Audio API") }}

متد `linearRampToValueAtTime()` از رابط {{ domxref("AudioParam") }} یک تغییر خطی تدریجی در مقدار `AudioParam` زمان‌بندی می‌کند. تغییر از زمان مشخص‌شده برای رویداد _قبلی_ شروع می‌شود، از یک رمپ خطی به مقدار جدید داده‌شده در پارامتر `value` پیروی می‌کند، و در زمان داده‌شده در پارامتر `endTime` به مقدار جدید می‌رسد.

## سینتکس

```js-nolint
linearRampToValueAtTime(value, endTime)
```

### پارامترها

- `value`
  - : یک عدد اعشاری (float) که نشان‌دهنده مقداری است که `AudioParam` تا زمان مشخص‌شده به آن رمپ می‌کند.
- `endTime`
  - : یک عدد double که زمان دقیق (به ثانیه) پس از شروع رمپ را نشان می‌دهد که تغییر مقدار در آن متوقف می‌شود.

### مقدار بازگشتی

یک ارجاع به این شیء `AudioParam`. در برخی مرورگرها، پیاده‌سازی‌های قدیمی‌تر این رابط {{jsxref('undefined')}} را برمی‌گردانند.

## مثال‌ها

در این مثال، یک منبع رسانه‌ای با دو دکمه کنترل داریم (برای مشاهده کد منبع، به [مخزن audio-param](https://github.com/mdn/webaudio-examples/tree/main/audio-param) مراجعه کنید یا [مثال را به‌صورت زنده ببینید](https://mdn.github.io/webaudio-examples/audio-param/).) وقتی این دکمه‌ها فشرده می‌شوند، `linearRampToValueAtTime()` برای محو کردن مقدار گین به ترتیب به 1.0 و پایین به 0 استفاده می‌شود. این برای افکت‌های محو شدن و ظاهر شدن بسیار مفید است، اگرچه اغلب گفته می‌شود {{domxref("AudioParam.exponentialRampToValueAtTime()")}} کمی طبیعی‌تر است.

```js
// create audio context
const audioCtx = new AudioContext();

// set basic variables for example
const myAudio = document.querySelector("audio");

const linearRampPlus = document.querySelector(".linear-ramp-plus");
const linearRampMinus = document.querySelector(".linear-ramp-minus");

// Create a MediaElementAudioSourceNode
// Feed the HTMLMediaElement into it
const source = audioCtx.createMediaElementSource(myAudio);

// Create a gain node and set its gain value to 0.5
const gainNode = audioCtx.createGain();

// connect the AudioBufferSourceNode to the gainNode
// and the gainNode to the destination
gainNode.gain.setValueAtTime(0, audioCtx.currentTime);
source.connect(gainNode);
gainNode.connect(audioCtx.destination);

// set buttons to do something onclick
linearRampPlus.onclick = () => {
  gainNode.gain.linearRampToValueAtTime(1.0, audioCtx.currentTime + 2);
};

linearRampMinus.onclick = () => {
  gainNode.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 2);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)