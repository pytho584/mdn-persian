---
title: "AudioParam: setTargetAtTime() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/setTargetAtTime"
translated_by: "n8n + AI"
---

---
title: "AudioParam: setTargetAtTime() method"
short-title: setTargetAtTime()
slug: Web/API/AudioParam/setTargetAtTime
page-type: web-api-instance-method
browser-compat: api.AudioParam.setTargetAtTime
---

{{ APIRef("Web Audio API") }}

متد `setTargetAtTime()` از رابط {{domxref("AudioParam")}} شروع تغییر تدریجی به سمت مقدار `AudioParam` را زمان‌بندی می‌کند. این متد برای بخش‌های decay یا release در پوشه‌های ADSR مفید است.

## نحو (Syntax)

```js-nolint
setTargetAtTime(target, startTime, timeConstant)
```

### پارامترها

- `target`
  - : مقداری که پارامتر در زمان شروع داده‌شده، انتقال به سمت آن را آغاز می‌کند.
- `startTime`
  - : زمانی که انتقال نمایی آغاز می‌شود، در همان سیستم مختصات زمانی {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}}. اگر این مقدار کمتر یا مساوی `AudioContext.currentTime` باشد، پارامتر بلافاصله تغییر می‌کند.
- `timeConstant`
  - : مقدار ثابت زمانی، بر حسب ثانیه، برای نزدیک‌شدن نمایی به مقدار هدف. هرچه این مقدار بزرگ‌تر باشد، انتقال کندتر خواهد بود.

### مقدار بازگشتی

ارجاعی به این شیء `AudioParam`. برخی پیاده‌سازی‌های قدیمی‌تر مرورگر از این رابط، {{jsxref('undefined')}} را برمی‌گردانند.

## توضیحات

تغییر در زمان مشخص‌شده در `startTime` آغاز می‌شود و به صورت نمایی به سمت مقدار داده‌شده توسط پارامتر `target` حرکت می‌کند. نرخ کاهش طبق پارامتر `timeConstant` نمایی است؛ بنابراین مقدار هرگز به طور کامل به `target` نمی‌رسد، اما پس از هر گام زمانی به طول `timeConstant`، مقدار به اندازه <math><semantics><mrow><mn>۱</mn><mo>-</mo><msup><mi>e</mi><mrow><mo>-</mo><mn>۱</mn></mrow></msup><mo>≈</mo><mn>۶۳٫۲</mn><mtext>٪</mtext></mrow><annotation encoding="TeX">1 - e^{-1} \approx 63.2%</annotation></semantics></math> به `target` نزدیک‌تر می‌شود. برای فرمول کامل (که از یک سیستم خطی مرتبه اول پیوسته در زمان استفاده می‌کند)، به [مشخصات Web Audio](https://webaudio.github.io/web-audio-api/#dom-audioparam-settargetattime) مراجعه کنید.

اگر قطعاً نیاز دارید که مقدار هدف را تا یک زمان مشخص برسید، می‌توانید از {{domxref("AudioParam.exponentialRampToValueAtTime()")}} استفاده کنید. با این حال، به دلایل ریاضی، آن متد زمانی کار نمی‌کند که مقدار فعلی یا مقدار هدف `0` باشد.

### انتخاب یک `timeConstant` خوب

همانطور که در بالا ذکر شد، مقدار به صورت نمایی تغییر می‌کند و هر `timeConstant` شما را ۶۳٫۲٪ دیگر به مقدار هدف نزدیک می‌کند. نیازی به نگرانی درباره رسیدن به مقدار هدف نیست؛ وقتی به اندازه کافی نزدیک شدید، تغییرات بعدی برای شنونده انسانی نامحسوس خواهد بود.

بسته به مورد استفاده شما، رسیدن به ۹۵٪ از مقدار هدف ممکن است کافی باشد؛ در آن صورت، می‌توانید `timeConstant` را یک سوم مدت زمان مورد نظر قرار دهید.

برای جزئیات بیشتر، جدول زیر را بررسی کنید که چگونه مقدار با گذشت زمان از ۰٪ به ۱۰۰٪ تغییر می‌کند.

| زمان پس از `startTime` | مقدار                                                       |
| ---------------------- | ----------------------------------------------------------- |
| `0 * timeConstant`     | ۰٪                                                          |
| `0.5 * timeConstant`   | ۳۹٫۳٪                                                       |
| `1 * timeConstant`     | ۶۳٫۲٪                                                       |
| `2 * timeConstant`     | ۸۶٫۵٪                                                       |
| `3 * timeConstant`     | ۹۵٫۰٪                                                       |
| `4 * timeConstant`     | ۹۸٫۲٪                                                       |
| `5 * timeConstant`     | ۹۹٫۳٪                                                       |
| `n * timeConstant`     | <math><semantics><mrow><mn>۱</mn></mrow></semantics></math> |

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mn>۱</mn><mo>-</mo><msup><mi>e</mi><mrow><mo>-</mo><mi>n</mi></mrow></msup></mrow><annotation encoding="TeX">1 - e^{-n}</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

## مثال‌ها

در این مثال، یک منبع رسانه‌ای با دو دکمه کنترلی داریم (برای کد منبع به [مخزن webaudio-examples](https://github.com/mdn/webaudio-examples/blob/main/audio-param/index.html) مراجعه کنید، یا [مثال زنده را ببینید](https://mdn.github.io/webaudio-examples/audio-param/)). وقتی این دکمه‌ها فشرده می‌شوند، `setTargetAtTime()` برای افزایش مقدار بهره به ۱٫۰ و کاهش آن به ۰ استفاده می‌شود، به طوری که اثر پس از ۱ ثانیه شروع می‌شود و مدت زمان اثر توسط timeConstant کنترل می‌شود.

```js
// create audio context
const audioCtx = new AudioContext();

// set basic variables for example
const myAudio = document.querySelector("audio");

const atTimePlus = document.querySelector(".at-time-plus");
const atTimeMinus = document.querySelector(".at-time-minus");

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
atTimePlus.onclick = () => {
  currGain = 1.0;
  gainNode.gain.setTargetAtTime(1.0, audioCtx.currentTime + 1, 0.5);
};

atTimeMinus.onclick = () => {
  currGain = 0;
  gainNode.gain.setTargetAtTime(0, audioCtx.currentTime + 1, 0.5);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)