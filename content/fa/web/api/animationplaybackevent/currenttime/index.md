---
title: "AnimationPlaybackEvent: currentTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationPlaybackEvent/currentTime"
translated_by: "n8n + AI"
---

---
title: "AnimationPlaybackEvent: currentTime property"
short-title: currentTime
slug: Web/API/AnimationPlaybackEvent/currentTime
page-type: web-api-instance-property
browser-compat: api.AnimationPlaybackEvent.currentTime
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`currentTime`** از رابط {{domxref("AnimationPlaybackEvent")}} زمان جاری انیمیشنی را نشان می‌دهد که رویداد را در لحظه‌ی قرار گرفتن رویداد در صف تولید کرده است. اگر انیمیشن در زمان تولید رویداد `idle` بوده باشد، این مقدار نامشخص خواهد بود.

## مقدار

عددی که زمان جاری را بر حسب میلی‌ثانیه نشان می‌دهد، یا `null`.

## کاهش دقت زمان

برای ارائه محافظت در برابر حملات زمان‌بندی و [اثر انگشت](/en-US/docs/Glossary/Fingerprinting)، ممکن است دقت `playbackEvent.currentTime` بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، تنظیم `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید، که در این صورت دقت برابر با ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` خواهد بود، هرکدام بزرگ‌تر باشد.

برای مثال، با کاهش دقت زمان، نتیجه‌ی `playbackEvent.currentTime` همیشه مضربی از 0.002 خواهد بود، یا با فعال بودن `privacy.resistFingerprinting`، مضربی از 0.1 (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
playbackEvent.currentTime;
// Might be:
// 23.404
// 24.192
// 25.514
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
playbackEvent.currentTime;
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

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationPlayBackEvent")}}