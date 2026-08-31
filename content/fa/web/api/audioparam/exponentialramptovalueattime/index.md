---
title: "AudioParam: exponentialRampToValueAtTime() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/exponentialRampToValueAtTime"
translated_by: "n8n + AI"
---

---
title: "AudioParam: exponentialRampToValueAtTime() method"
short-title: exponentialRampToValueAtTime()
slug: Web/API/AudioParam/exponentialRampToValueAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.exponentialRampToValueAtTime
---

{{ APIRef("Web Audio API") }}

متد **`exponentialRampToValueAtTime()`** از رابط {{domxref("AudioParam")}} یک تغییر تدریجی نمایی در مقدار {{domxref("AudioParam")}} را برنامه‌ریزی می‌کند. تغییر از زمان مشخص‌شده برای رویداد _قبلی_ شروع می‌شود، از یک شیب نمایی به مقدار جدید داده شده در پارامتر `value` پیروی می‌کند و در زمان داده شده در پارامتر `endTime` به مقدار جدید می‌رسد.

> [!NOTE]
> شیب‌های نمایی در تغییر فرکانس‌ها یا نرخ‌های پخش نسبت به شیب‌های خطی مفیدتر در نظر گرفته می‌شوند، زیرا نحوه عملکرد گوش انسان به این صورت است.

## Syntax

```js-nolint
exponentialRampToValueAtTime(value, endTime)
```

### Parameters

- `value`
  - : یک عدد اعشاری که نشان‌دهنده مقداری است که `AudioParam` تا زمان داده شده به آن شیب می‌کند.
- `endTime`
  - : یک عدد اعشاری (دابل) که نشان‌دهنده زمان دقیق (بر حسب ثانیه) پس از شروع شیب است که تغییر مقدار متوقف می‌شود.

### Return value

یک ارجاع به این شیء `AudioParam`. در برخی مرورگرها، پیاده‌سازی‌های قدیمی‌تر این رابط {{jsxref('undefined')}} را برمی‌گردانند.

## Examples

در این مثال، ما یک منبع رسانه با دو دکمه کنترل داریم (برای کد منبع به [مخزن audio-param](https://github.com/mdn/webaudio-examples/tree/main/audio-param) مراجعه کنید، یا [مثال را به صورت زنده](https://mdn.github.io/webaudio-examples/audio-param/) مشاهده کنید.) هنگامی که این دکمه‌ها فشرده می‌شوند، `exponentialRampToValueAtTime()` برای افزایش مقدار بهره به 1.0 و کاهش آن به 0 به ترتیب استفاده می‌شود. این برای افکت‌های محو شدن (fade in/fade out) بسیار مفید است:

```js
// create audio context
const audioCtx = new AudioContext();

// set basic variables for example
const myAudio = document.querySelector("audio");

const expRampPlus = document.querySelector(".exp-ramp-plus");
const expRampMinus = document.querySelector(".exp-ramp-minus");

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
expRampPlus.onclick = () => {
  gainNode.gain.exponentialRampToValueAtTime(1.0, audioCtx.currentTime + 2);
};

expRampMinus.onclick = () => {
  gainNode.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 2);
};
```

> [!NOTE]
> یک مقدار 0.01 برای مقداری که در آخرین تابع به آن شیب می‌کند به جای 0 استفاده شده است، زیرا اگر 0 استفاده شود خطای _رشته نامعتبر یا غیرقانونی_ پرتاب می‌شود — مقدار باید مثبت باشد.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)