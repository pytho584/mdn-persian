---
title: "OfflineAudioContext: OfflineAudioContext() constructor"
---

---
title: "OfflineAudioContext: OfflineAudioContext() constructor"
short-title: OfflineAudioContext()
slug: Web/API/OfflineAudioContext/OfflineAudioContext
page-type: web-api-constructor
browser-compat: api.OfflineAudioContext.OfflineAudioContext
---

{{APIRef("Web Audio API")}}

سازندهٔ **`OfflineAudioContext()`** که بخشی از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) است، یک نمونهٔ جدید از {{domxref("OfflineAudioContext")}} ایجاد و بازمی‌گرداند. سپس می‌توان از این نمونه برای رندر صدا به یک {{domxref("AudioBuffer")}} به‌جای یک دستگاه خروجی صدا استفاده کرد.

## نحو

```js-nolint
new OfflineAudioContext(options)

new OfflineAudioContext(numberOfChannels, length, sampleRate)
```

### پارامترها

می‌توانید پارامترهای سازندهٔ `OfflineAudioContext()` را یا به‌عنوان همان مجموعه‌ای از پارامترها که ورودی‌های متد {{domxref("BaseAudioContext.createBuffer")}} هستند مشخص کنید، یا با عبور دادن این پارامترها در یک شیء `options`. در هر صورت، پارامترهای تکتک یکسان هستند.

- `numberOfChannels`
  - : یک عدد صحیح که تعداد کانال‌هایی را مشخص می‌کند که {{domxref("AudioBuffer")}} حاصل باید داشته باشد.
- `length`
  - : یک عدد صحیح که اندازهٔ بافری را که برای زمینهٔ صوتی ساخته می‌شود، بر حسب sample-frame (چارچوب نمونه) مشخص می‌کند. هر sample-frame واحدی است که می‌تواند یک نمونهٔ واحد از داده‌های صوتی را برای هر کانال در داده‌های صوتی در خود جای دهد. برای مثال، یک بافر ۵ ثانیه‌ای با `sampleRate` برابر ۴۸۰۰۰ هرتز، طولی برابر `5 * 48000 = 240000` sample-frame خواهد داشت.
- `sampleRate`
  - : نرخ نمونه‌برداری داده‌های صوتی خطی بر حسب sample-frame در ثانیه. همهٔ عامل‌های کاربر (user agent) ملزم به پشتیبانی از بازهٔ ۸۰۰۰ هرتز تا ۹۶۰۰۰ هرتز هستند و ممکن است بازهٔ گسترده‌تری را نیز پشتیبانی کنند. رایج‌ترین نرخ استفاده‌شده ۴۴۱۰۰ هرتز است که نرخ نمونه‌برداری مورد استفاده در صوتی CD است.

توجه به این نکته مهم است که در حالی که می‌توانید یک {{domxref("AudioContext")}} جدید با استفاده از سازندهٔ {{domxref("AudioContext.AudioContext()", "AudioContext()")}} و بدون هیچ آرگومانی ایجاد کنید، سازندهٔ `OfflineAudioContext()` به سه آرگومان نیاز دارد، زیرا باید یک `AudioBuffer` بسازد. این کار دقیقاً به همان شیوه‌ای عمل می‌کند که هنگام ایجاد یک {{domxref("AudioBuffer")}} جدید با متد {{domxref("BaseAudioContext.createBuffer")}} انجام می‌شود. برای جزئیات بیشتر، [بافرهای صوتی: فریم‌ها، نمونه‌ها و کانال‌ها](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_buffers_frames_samples_and_channels) را از راهنمای [مفاهیم پایه](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API) ما بخوانید.

### مقدار بازگشتی

یک شیء جدید {{domxref("OfflineAudioContext")}} که `AudioBuffer` مرتبط با آن مطابق درخواست پیکربندی شده است.

مانند یک `AudioContext` معمولی، یک `OfflineAudioContext` می‌تواند هدف رویدادها باشد و بنابراین رابط {{domxref("EventTarget")}} را پیاده‌سازی می‌کند.

## مثال‌ها

```js
const offlineCtx = new OfflineAudioContext({
  numberOfChannels: 2,
  length: 44100 * 40,
  sampleRate: 44100,
});
const source = offlineCtx.createBufferSource();
// …
```

برای یک مثال کامل و قابل اجرا، مخزن گیت‌هاب [offline-audio-context-promise](https://mdn.github.io/webaudio-examples/offline-audio-context-promise/) ما را ببینید (همچنین [کد منبع](https://github.com/mdn/webaudio-examples/blob/main/offline-audio-context-promise/index.html) را ببینید.)

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}