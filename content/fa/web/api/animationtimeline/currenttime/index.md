```markdown
---
title: "AnimationTimeline: currentTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationTimeline/currentTime"
translated_by: "n8n + AI"
---

---
title: "AnimationTimeline: currentTime property"
short-title: currentTime
slug: Web/API/AnimationTimeline/currentTime
page-type: web-api-instance-property
browser-compat: api.AnimationTimeline.currentTime
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`currentTime`** در رابط {{domxref("AnimationTimeline")}} از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)، زمان فعلی خط زمانی را بر حسب میلی‌ثانیه برمی‌گرداند، یا اگر خط زمانی غیرفعال باشد، مقدار `null` را برمی‌گرداند.

## مقدار

عددی که زمان فعلی خط زمانی را بر حسب میلی‌ثانیه نشان می‌دهد، یا اگر خط زمانی غیرفعال باشد، مقدار `null`.

## دقت کاهش‌یافته زمان

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت دیجیتال](/en-US/docs/Glossary/Fingerprinting)، دقت `animationTimeline.currentTime` ممکن است بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، اولویت `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و مقدار پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید، که در این صورت دقت ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`، هر کدام بزرگ‌تر است، خواهد بود.

برای مثال، با دقت کاهش‌یافته زمان، نتیجه `animationTimeline.currentTime` همیشه مضربی از ۰٫۰۰۲ خواهد بود، یا با فعال بودن `privacy.resistFingerprinting`، مضربی از ۰٫۱ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
animationTimeline.currentTime;
// Might be:
// 23.404
// 24.192
// 25.514
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
animationTimeline.currentTime;
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
- {{domxref("AnimationTimeline")}}
- {{domxref("DocumentTimeline")}} این ویژگی را به ارث می‌برد
- {{domxref("Document.timeline")}} یک شیء خط زمانی برمی‌گرداند که این ویژگی را به ارث می‌برد
```