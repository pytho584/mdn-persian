---
title: "Animation: currentTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/currentTime"
translated_by: "n8n + AI"
---

---
title: "Animation: currentTime property"
short-title: currentTime
slug: Web/API/Animation/currentTime
page-type: web-api-instance-property
browser-compat: api.Animation.currentTime
---

{{APIRef("Web Animations")}}

خاصیت **`Animation.currentTime`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)، مقدار زمانی جاری انیمیشن را بر حسب میلی‌ثانیه بازمی‌گرداند و تنظیم می‌کند، چه در حال اجرا باشد چه متوقف شده باشد.

اگر انیمیشن فاقد {{domxref("AnimationTimeline", "timeline")}} باشد، غیرفعال باشد، یا هنوز پخش نشده باشد، مقدار بازگشتی `currentTime` برابر با `null` است.

## مقدار

عددی که زمان جاری را بر حسب میلی‌ثانیه نشان می‌دهد، یا `null` برای غیرفعال کردن انیمیشن.

## مثال‌ها

در بازی [Drink Me/Eat Me game](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010)، ارتفاع آلیس به‌گونه‌ای انیمیشن‌سازی می‌شود که بتواند از کوچک به بزرگ یا از بزرگ به کوچک تغییر کند. در شروع بازی، ارتفاع او با تنظیم `currentTime` انیمیشنش بر روی نصف مدت زمان `KeyframeEffect`، بین دو حالت حدی قرار می‌گیرد:

```js
aliceChange.currentTime = aliceChange.effect.timing.duration / 2;
```

یک روش عمومی‌تر برای پرش به نشانه ۵۰٪ یک انیمیشن به این صورت است:

```js
animation.currentTime =
  animation.effect.getComputedTiming().delay +
  animation.effect.getComputedTiming().activeDuration / 2;
```

## دقت زمانی کاهش‌یافته

به‌منظور محافظت در برابر حملات زمان‌بندی و [fingerprinting](/en-US/docs/Glossary/Fingerprinting)، ممکن است دقت `animation.currentTime` بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، ترجیح `privacy.reduceTimerPrecision` به‌صورت پیش‌فرض فعال است و پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید؛ در این صورت دقت، ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`، هر کدام بزرگ‌تر باشد، خواهد بود.

برای مثال، با دقت زمانی کاهش‌یافته، نتیجه `animation.currentTime` همیشه مضربی از ۰٫۰۰۲، یا - با فعال بودن `privacy.resistFingerprinting` - مضربی از ۰٫۱ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
animation.currentTime;
// Might be:
// 23.404
// 24.192
// 25.514
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
animation.currentTime;
// Might be:
// 49.8
// 50.6
// 51.7
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Animation")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.startTime")}} برای زمانی که یک انیمیشن برنامه‌ریزی شده تا شروع شود.
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)