---
title: "AudioParam: setValueCurveAtTime() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/setValueCurveAtTime"
translated_by: "n8n + AI"
---

---
title: "AudioParam: setValueCurveAtTime() method"
short-title: setValueCurveAtTime()
slug: Web/API/AudioParam/setValueCurveAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.setValueCurveAtTime
---

{{APIRef("Web Audio API")}}

متد **`setValueCurveAtTime()`** از رابط {{domxref("AudioParam")}}، تغییر مقدار پارامتر را طبق یک منحنی تعریف‌شده توسط یک لیست از مقادیر زمان‌بندی می‌کند.

این منحنی یک درون‌یابی خطی بین دنباله‌ای از مقادیر تعریف‌شده در یک آرایه از اعداد اعشاری است که به‌گونه‌ای مقیاس‌بندی می‌شوند تا در بازه زمانی مشخص‌شده از `startTime` و یک مدت زمان خاص قرار گیرند.

## نحو

```js-nolint
setValueCurveAtTime(values, startTime, duration)
```

### پارامترها

- `values`
  - : آرایه‌ای از اعداد اعشاری که منحنی مقداری را نشان می‌دهد که {{domxref("AudioParam")}} در طول `duration` مشخص از آن عبور می‌کند. هر مقدار در آرایه باید یک عدد متناهی باشد؛ اگر هر مقداری `NaN`، `Infinity` یا `-Infinity` باشد، یک استثنای {{jsxref("TypeError")}} پرتاب می‌شود.
- `startTime`
  - : یک عدد اعشاری که زمان (بر حسب ثانیه) پس از ایجاد اولین {{domxref("AudioContext")}} را نشان می‌دهد که تغییر در مقدار رخ خواهد داد. اگر این مقدار کمتر از {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} باشد، به `currentTime` محدود می‌شود.
- `duration`
  - : یک عدد اعشاری که کل زمان (بر حسب ثانیه) را نشان می‌دهد که در طی آن `value` پارامتر طبق منحنی مشخص شده تغییر می‌کند. مقادیر مشخص‌شده به طور مساوی در طول این مدت زمان توزیع می‌شوند.

### مقدار بازگشتی

یک ارجاع به این شیء `AudioParam`. برخی پیاده‌سازی‌های قدیمی‌تر مرورگر از این رابط `undefined` را برمی‌گردانند.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر آرایه `values` مشخص‌شده کمتر از ۲ آیتم داشته باشد، پرتاب می‌شود.
- {{jsxref("RangeError")}}
  - : اگر `startTime` مشخص‌شده منفی یا غیرمتناهی باشد، یا `duration` یک عدد متناهی و مثبت دقیق نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر یک یا چند مقدار در آرایه `values` غیرمتناهی باشد، پرتاب می‌شود. مقادیر غیرمتناهی عبارتند از `NaN`، `Infinity` و `-Infinity`.

## نکات استفاده

هنگامی که مقدار پارامتر از دنباله منحنی پیروی می‌کند، مقدار آن تضمین می‌شود که با آخرین مقدار در مجموعه مقادیر مشخص‌شده در پارامتر `values` مطابقت داشته باشد.

> [!NOTE]
> برخی پیاده‌سازی‌های اولیه Web Audio API این مورد را تضمین نمی‌کردند که منجر به نتایج غیرمنتظره می‌شد.

## مثال‌ها

در این مثال، ما یک منبع رسانه‌ای با یک دکمه داریم (برای کد منبع به [مخزن webaudio-examples](https://github.com/mdn/webaudio-examples/blob/main/audio-param/index.html) مراجعه کنید، یا [مثال زنده](https://mdn.github.io/webaudio-examples/audio-param/) را مشاهده کنید). هنگامی که این دکمه فشار داده می‌شود، از `setValueCurveAtTime()` برای تغییر مقدار بهره بین مقادیر موجود در آرایه `waveArray` استفاده می‌شود:

```js
// ایجاد زمینه صوتی
const audioCtx = new AudioContext();

// تنظیم متغیرهای پایه برای مثال
const myAudio = document.querySelector("audio");

const valueCurve = document.querySelector(".value-curve");

// ایجاد یک MediaElementAudioSourceNode
// تغذیه HTMLMediaElement به آن
const source = audioCtx.createMediaElementSource(myAudio);

// ایجاد یک گره بهره و تنظیم مقدار بهره آن به 0.5
const gainNode = audioCtx.createGain();
gainNode.gain.value = 0.5;
const currGain = gainNode.gain.value;

// اتصال AudioBufferSourceNode به gainNode
// و gainNode به مقصد
source.connect(gainNode);
gainNode.connect(audioCtx.destination);

// تنظیم دکمه برای انجام کار در کلیک

const waveArray = new Float32Array(9);
waveArray[0] = 0.5;
waveArray[1] = 1;
waveArray[2] = 0.5;
waveArray[3] = 0;
waveArray[4] = 0.5;
waveArray[5] = 1;
waveArray[6] = 0.5;
waveArray[7] = 0;
waveArray[8] = 0.5;

valueCurve.onclick = () => {
  gainNode.gain.setValueCurveAtTime(waveArray, audioCtx.currentTime, 2);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

نسخه‌های قبل از Chrome 46 به جای درون‌یابی خطی از نزدیک‌ترین همسایه استفاده می‌کنند.

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)