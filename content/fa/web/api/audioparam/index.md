---
title: "AudioParam"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam"
translated_by: "n8n + AI"
---

---
title: AudioParam
slug: Web/API/AudioParam
page-type: web-api-interface
browser-compat: api.AudioParam
---

{{APIRef("Web Audio API")}}

رابط `AudioParam` در Web Audio API پارامتری مرتبط با صوت را نشان می‌دهد، معمولاً پارامتری از {{domxref("AudioNode")}} (مانند {{ domxref("GainNode.gain") }}).

یک `AudioParam` می‌تواند روی یک مقدار خاص یا تغییر مقدار تنظیم شود و می‌توان زمان‌بندی کرد که در زمانی خاص و طبق الگوی خاصی رخ دهد.

هر `AudioParam` فهرستی از رویدادها دارد که در ابتدا خالی است و مشخص می‌کند چه زمانی و چگونه مقادیر تغییر می‌کنند. وقتی این فهرست خالی نیست، تغییرات با استفاده از ویژگی‌های `AudioParam.value` نادیده گرفته می‌شوند. این فهرست رویدادها به ما امکان می‌دهد تغییراتی را که باید در زمان‌های بسیار دقیق رخ دهند، با استفاده از منحنی‌های اتوماسیون مبتنی بر زمان‌بندی دلخواه زمان‌بندی کنیم. زمان استفاده‌شده همان است که در {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} تعریف شده است.

## انواع AudioParam

دو نوع `AudioParam` وجود دارد: پارامترهای _a-rate_ و _k-rate_. هر {{domxref("AudioNode")}} در مشخصات تعریف می‌کند که کدام یک از پارامترهای آن _a-rate_ یا _k-rate_ هستند.

### a-rate

یک `AudioParam` از نوع _a-rate_ مقدار پارامتر صوتی فعلی را برای هر [sample frame](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_buffers_frames_samples_and_channels) از سیگنال صوتی می‌گیرد.

### k-rate

یک `AudioParam` از نوع _k-rate_ از همان مقدار پارامتر صوتی اولیه برای کل بلوک پردازش‌شده استفاده می‌کند؛ یعنی ۱۲۸ فریم نمونه. به عبارت دیگر، همان مقدار برای هر فریم در صوتی که توسط گره پردازش می‌شود اعمال می‌شود.

## ویژگی‌های نمونه

- {{domxref("AudioParam.defaultValue")}} {{ReadOnlyInline}}
  - مقدار اولیه ویژگی را که توسط {{domxref("AudioNode")}} خاص ایجادکننده `AudioParam` تعریف شده است، نشان می‌دهد.
- {{domxref("AudioParam.maxValue")}} {{ReadOnlyInline}}
  - حداکثر مقدار ممکن برای محدوده اسمی (موثر) پارامتر را نشان می‌دهد.
- {{domxref("AudioParam.minValue")}} {{ReadOnlyInline}}
  - حداقل مقدار ممکن برای محدوده اسمی (موثر) پارامتر را نشان می‌دهد.
- {{domxref("AudioParam.value")}}
  - مقدار فعلی پارامتر را در زمان جاری نشان می‌دهد؛ در ابتدا روی مقدار {{domxref("AudioParam.defaultValue", "defaultValue")}} تنظیم شده است.

## روش‌های نمونه

- {{domxref("AudioParam.setValueAtTime()")}}
  - یک تغییر آنی در مقدار `AudioParam` را در زمان دقیقی، که نسبت به {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} سنجیده می‌شود، زمان‌بندی می‌کند. مقدار جدید توسط پارامتر `value` داده می‌شود.
- {{domxref("AudioParam.linearRampToValueAtTime()")}}
  - یک تغییر خطی تدریجی در مقدار `AudioParam` را زمان‌بندی می‌کند. تغییر از زمان مشخص‌شده برای رویداد _قبلی_ شروع می‌شود، از یک شیب خطی به مقدار جدید داده‌شده در پارامتر `value` پیروی می‌کند و در زمان داده‌شده در پارامتر `endTime` به مقدار جدید می‌رسد.
- {{domxref("AudioParam.exponentialRampToValueAtTime()")}}
  - یک تغییر نمایی تدریجی در مقدار `AudioParam` را زمان‌بندی می‌کند. تغییر از زمان مشخص‌شده برای رویداد _قبلی_ شروع می‌شود، از یک شیب نمایی به مقدار جدید داده‌شده در پارامتر `value` پیروی می‌کند و در زمان داده‌شده در پارامتر `endTime` به مقدار جدید می‌رسد.
- {{domxref("AudioParam.setTargetAtTime()")}}
  - آغاز تغییری در مقدار `AudioParam` را زمان‌بندی می‌کند. تغییر از زمان مشخص‌شده در `startTime` شروع می‌شود و به‌صورت نمایی به سمت مقدار داده‌شده توسط پارامتر `target` حرکت می‌کند. نرخ کاهش نمایی توسط پارامتر `timeConstant` تعریف می‌شود که زمانی بر حسب ثانیه است.
- {{domxref("AudioParam.setValueCurveAtTime()")}}
  - مقادیر `AudioParam` را زمان‌بندی می‌کند تا از مجموعه مقادیری پیروی کنند که توسط آرایه‌ای از اعداد اعشاری مقیاس‌بندی‌شده برای تطبیق با بازه داده‌شده تعریف شده‌اند، از زمان شروع معین شروع شده و مدت‌زمان معینی را پوشش می‌دهند.
- {{domxref("AudioParam.cancelScheduledValues()")}}
  - همه تغییرات آینده زمان‌بندی‌شده برای `AudioParam` را لغو می‌کند.
- {{domxref("AudioParam.cancelAndHoldAtTime()")}}
  - همه تغییرات آینده زمان‌بندی‌شده برای `AudioParam` را لغو می‌کند، اما مقدار آن را در یک زمان معین نگه می‌دارد تا زمانی که تغییرات بیشتری با استفاده از روش‌های دیگر انجام شود.

## مثال‌ها

ابتدا، یک مثال ساده که یک {{domxref("GainNode")}} را با مقدار `gain` تنظیم‌شده نشان می‌دهد. `gain` نمونه‌ای از _a-rate_ `AudioParam` است، زیرا مقدار می‌تواند به‌طور بالقوه برای هر فریم نمونه از صوت متفاوت تنظیم شود.

```js
const audioCtx = new AudioContext();

const gainNode = audioCtx.createGain();
gainNode.gain.value = 0;
```

در ادامه، مثالی که یک {{ domxref("DynamicsCompressorNode") }} را با تغییر برخی مقادیر پارامتر نشان می‌دهد. این‌ها نمونه‌هایی از انواع _k-rate_ `AudioParam` هستند، زیرا مقادیر برای کل بلوک صوتی به‌طور یکجا تنظیم می‌شوند.

```js
const compressor = audioCtx.createDynamicsCompressor();
compressor.threshold.setValueAtTime(-50, audioCtx.currentTime);
compressor.knee.setValueAtTime(40, audioCtx.currentTime);
compressor.ratio.setValueAtTime(12, audioCtx.currentTime);
compressor.attack.setValueAtTime(0, audioCtx.currentTime);
compressor.release.setValueAtTime(0.25, audioCtx.currentTime);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)