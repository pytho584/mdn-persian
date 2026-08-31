---
title: "AudioParam: value property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioParam/value"
translated_by: "n8n + AI"
---

---
title: "AudioParam: value property"
short-title: value
slug: Web/API/AudioParam/value
page-type: web-api-instance-property
browser-compat: api.AudioParam.value
---

{{APIRef("Web Audio API")}}

ویژگی **`value`** از رابط {{domxref("AudioParam")}} مقدار این `AudioParam` را در زمان فعلی دریافت یا تنظیم می‌کند. در ابتدا، مقدار روی {{domxref("AudioParam.defaultValue")}} تنظیم می‌شود.

تنظیم `value` همان اثر فراخوانی {{domxref("AudioParam.setValueAtTime")}} را با زمانی دارد که توسط ویژگی {{domxref("BaseAudioContext/currentTime", "currentTime")}} از `AudioContext` بازگردانده می‌شود.

## مقدار

یک {{jsxref("Number")}} ممیز شناور که مقدار پارامتر را در زمان فعلی نشان می‌دهد. این مقدار بین مقادیر مشخص‌شده توسط ویژگی‌های {{domxref("AudioParam.minValue", "minValue")}} و {{domxref("AudioParam.maxValue", "maxValue")}} خواهد بود.

## توضیحات

### دقت و تغییرپذیری مقدار

نوع داده‌ای که به صورت داخلی برای ذخیره‌سازی `value` استفاده می‌شود، عدد ممیز شناور تک‌دقت (۳۲ بیتی) است، در حالی که جاوااسکریپت از اعداد ممیز شناور با دقت مضاعف ۶۴ بیتی استفاده می‌کند. در نتیجه، مقداری که از ویژگی `value` می‌خوانید ممکن است همیشه دقیقاً برابر با مقداری که تنظیم کرده‌اید نباشد.

این مثال را در نظر بگیرید:

```js
const source = new AudioBufferSourceNode(/* … */);
const rate = 5.3;
source.playbackRate.value = rate;
console.log(source.playbackRate.value === rate);
```

خروجی لاگ `false` خواهد بود، زیرا پارامتر نرخ پخش، `rate`، به نزدیک‌ترین عدد ممیز شناور ۳۲ بیتی به ۵.۳ تبدیل شده است که ۵.300000190734863 را به دست می‌دهد. یک راه‌حل استفاده از روش {{jsxref("Math.fround()")}} است که مقدار تک‌دقت معادل با مقدار جاوااسکریپت ۶۴ بیتی مشخص‌شده را برمی‌گرداند — هنگام تنظیم `value`، به این صورت:

```js
const source = new AudioBufferSourceNode(/* … */);
const rate = Math.fround(5.3);
source.playbackRate.value = rate;
console.log(source.playbackRate.value === rate);
```

در این حالت، خروجی لاگ `true` خواهد بود.

### مقدار ویژگی که با گذشت زمان تغییر می‌کند

مقدار یک `AudioParam` می‌تواند ثابت باشد یا با گذشت زمان تغییر کند. این توسط getter مربوط به `value` منعکس می‌شود، که مقدار پارامتر را از آخرین **کوانتوم رندر** موتور رندر صوتی، یا لحظه‌ای که بافرهای صوتی پردازش و به‌روزرسانی می‌شوند، برمی‌گرداند. علاوه بر پردازش بافرهای صوتی، هر کوانتوم رندر، `value` هر `AudioParam` را در صورت نیاز با توجه به زمان فعلی و هر تغییر زمان‌بندی‌شده در مقدار پارامتر به‌روزرسانی می‌کند.

هنگام ایجاد اولیه پارامتر، مقدار آن روی مقدار پیش‌فرض خود، که توسط {{domxref("AudioParam.defaultValue")}} داده می‌شود، تنظیم می‌شود. این مقدار پارامتر در زمان ۰.۰ ثانیه است و تا اولین کوانتوم رندری که در آن مقدار تغییر می‌کند، مقدار پارامتر باقی می‌ماند.

در طول هر کوانتوم رندر، مرورگر کارهای زیر را برای مدیریت مقدار یک پارامتر انجام می‌دهد:

- اگر setter مربوط به `value` استفاده شده باشد، مقدار پارامتر به مقدار داده‌شده تغییر می‌کند.
- اگر زمان فعلی برابر یا بیشتر از زمانی باشد که توسط فراخوانی قبلی {{domxref("AudioParam.setValueAtTime", "setValueAtTime()")}} مشخص شده است، `value` به مقداری که به `setValueAtTime()` ارسال شده تغییر می‌کند.
- اگر هر یک از روش‌های تغییر مقدار پلکانی یا شیب‌دار فراخوانی شده باشند و زمان فعلی در محدوده زمانی باشد که تغییر پلکانی باید رخ دهد، مقدار بر اساس الگوریتم مناسب به‌روزرسانی می‌شود. این روش‌های تغییر مقدار شیب‌دار یا پلکانی شامل {{domxref("AudioParam.linearRampToValueAtTime", "linearRampToValueAtTime()")}}، {{domxref("AudioParam.setTargetAtTime", "setTargetAtTime()")}} و {{domxref("AudioParam.setValueCurveAtTime", "setValueCurveAtTime()")}} هستند.

بنابراین، `value` یک پارامتر به گونه‌ای نگهداری می‌شود که وضعیت پارامتر را در طول زمان به دقت منعکس کند.

## مثال‌ها

این مثال به‌طور آنی حجم یک {{domxref("GainNode")}} را به ۴۰٪ تغییر می‌دهد.

```js
const audioCtx = new AudioContext();
const gainNode = audioCtx.createGain();
gainNode.gain.value = 0.4;
// which is identical to:
gainNode.gain.setValueAtTime(0.4, audioCtx.currentTime);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)