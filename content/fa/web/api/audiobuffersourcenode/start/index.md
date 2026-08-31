---
title: "AudioBufferSourceNode: start() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/start"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: start() method"
short-title: start()
slug: Web/API/AudioBufferSourceNode/start
page-type: web-api-instance-method
browser-compat: api.AudioBufferSourceNode.start
---

{{ APIRef("Web Audio API") }}

متد `start()` از رابط {{ domxref("AudioBufferSourceNode") }} برای زمان‌بندی پخش داده‌های صوتی موجود در بافر، یا شروع فوری پخش استفاده می‌شود.

## سینتکس

```js-nolint
start(when)
start(when, offset)
start(when, offset, duration)
```

### پارامترها

- `when` {{optional_inline}}
  - : زمانی بر حسب ثانیه که صدا باید شروع به پخش کند، در همان سیستم مختصات زمانی که توسط {{domxref("AudioContext")}} استفاده می‌شود. اگر `when` کمتر از {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} باشد یا برابر ۰ باشد، صدا بلافاصله شروع به پخش می‌کند. **مقدار پیش‌فرض ۰ است.**
- `offset` {{optional_inline}}
  - : یک آفست، که به صورت تعداد ثانیه در همان سیستم مختصات زمانی `AudioContext` مشخص می‌شود، برای زمانی در بافر صوتی که پخش باید از آنجا شروع شود. برای مثال، برای شروع پخش از وسط یک کلیپ صوتی ۱۰ ثانیه‌ای، `offset` باید ۵ باشد. مقدار پیش‌فرض، ۰، پخش را از ابتدای بافر صوتی شروع می‌کند، و آفست‌هایی که از انتهای صوتی که قرار است پخش شود (بر اساس {{domxref("AudioBuffer.duration", "duration")}} بافر صوتی و/یا ویژگی {{domxref("AudioBufferSourceNode.loopEnd", "loopEnd")}}) عبور کنند، به‌صورت بی‌صدا به حداکثر مقدار مجاز محدود می‌شوند. محاسبه آفست در صدا با استفاده از نرخ نمونه طبیعی بافر صدا انجام می‌شود، نه نرخ پخش فعلی، بنابراین حتی اگر صدا با دو برابر سرعت عادی خود در حال پخش باشد، نقطه میانی یک بافر صوتی ۱۰ ثانیه‌ای همچنان ۵ است.
- `duration` {{optional_inline}}
  - : مدت زمان داده صوتی که باید پخش شود، که به صورت ثانیه‌ای از کل محتوای بافر مشخص می‌شود. اگر این پارامتر مشخص نشود، صدا تا رسیدن به پایان طبیعی خود پخش می‌شود یا با استفاده از متد {{domxref("AudioScheduledSourceNode.stop", "stop()")}} متوقف می‌شود. این مقدار مستقل از {{domxref("AudioBufferSourceNode.playbackRate")}} است، بنابراین برای مثال، یک `duration` برابر ۲ ثانیه با `playbackRate` برابر ۲، ۲ ثانیه از منبع را پخش می‌کند و خروجی صوتی ۱ ثانیه‌ای تولید می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- {{jsxref("TypeError")}}
  - : زمانی پرتاب می‌شود که مقدار منفی برای یک یا چند مورد از سه پارامتر زمانی مشخص شده باشد. لطفاً سعی نکنید در قوانین فیزیک زمانی دستکاری کنید.
- `InvalidStateError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `start()` قبلاً فراخوانی شده باشد. شما فقط می‌توانید این تابع را یک بار در طول عمر یک `AudioBufferSourceNode` فراخوانی کنید.

## مثال‌ها

ساده‌ترین مثال فقط پخش بافر صوتی را از ابتدا شروع می‌کند — در این حالت نیازی به مشخص کردن هیچ پارامتری نیست:

```js
source.start();
```

مثال پیچیده‌تر زیر، ۱ ثانیه بعد از الآن، پخش ۱۰ ثانیه صدا را از ۳ ثانیه‌ای بافر صوتی شروع می‌کند.

```js
source.start(audioCtx.currentTime + 1, 3, 10);
```

> [!NOTE]
> برای یک مثال کامل‌تر که کاربرد `start()` را نشان می‌دهد، به مثال {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}} مراجعه کنید. همچنین می‌توانید [مثال را به صورت زنده مشاهده کنید](https://mdn.github.io/webaudio-examples/decode-audio-data/promise/) و [سورس مثال را](https://github.com/mdn/webaudio-examples/tree/main/decode-audio-data) ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)