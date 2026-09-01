---
title: "HTMLMediaElement: currentTime property"
short-title: currentTime
slug: Web/API/HTMLMediaElement/currentTime
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.currentTime
---

{{APIRef("HTML DOM")}}

خاصیت **`currentTime`** در رابط {{domxref("HTMLMediaElement")}} زمان پخش جاری را بر حسب ثانیه مشخص می‌کند.

تغییر مقدار `currentTime` باعث می‌شود رسانه به زمان جدید منتقل شود (Seek).

## مقدار

یک عدد اعشاری با دقت دو برابر که زمان پخش جاری را بر حسب ثانیه نشان می‌دهد.

اگر رسانه هنوز در حال پخش نیست، مقدار `currentTime` موقعیت زمانی درون رسانه را مشخص می‌کند که پس از فراخوانی متد {{domxref("HTMLMediaElement.play", "play()")}} پخش از آن آغاز خواهد شد.

تنظیم `currentTime` به یک مقدار جدید، در صورت در دسترس بودن رسانه، آن را به زمان داده‌شده منتقل می‌کند.

برای رسانه‌هایی که طول مدت مشخصی ندارند - مانند رسانه‌هایی که به صورت زنده پخش می‌شوند - ممکن است مرورگر نتواند بخش‌هایی از رسانه را که از بافر رسانه منقضی شده‌اند به دست آورد. همچنین، رسانه‌ای که خط زمانی آن از ۰ ثانیه شروع نمی‌شود را نمی‌توان به زمانی قبل از اولین زمان خط زمانی آن منتقل کرد.

طول مدت رسانه بر حسب ثانیه را می‌توان با استفاده از خاصیت {{domxref("HTMLMediaElement.duration", "duration")}} تعیین کرد.

## مثال‌ها

```js
const video = document.createElement("video");
console.log(video.currentTime);
```

## نکات استفاده

### کاهش دقت زمان

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت](/fa/docs/Glossary/Fingerprinting)، دقت `video.currentTime` ممکن است بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، گزینه `privacy.reduceTimerPrecision` به طور پیش‌فرض فعال است و مقدار پیش‌فرض آن ۲ میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید، که در این صورت دقت ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` خواهد بود، هر کدام بزرگ‌تر باشد.

به عنوان مثال، با کاهش دقت زمان، نتیجه `video.currentTime` همیشه مضربی از ۰٫۰۰۲ یا مضربی از ۰٫۱ (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`) با فعال بودن `privacy.resistFingerprinting` خواهد بود.

```js
// کاهش دقت زمان (2ms) در فایرفاکس 60
video.currentTime;
// ممکن است:
// 23.404
// 24.192
// 25.514
// …

// کاهش دقت زمان با فعال بودن `privacy.resistFingerprinting`
video.currentTime;
// ممکن است:
// 49.8
// 50.6
// 51.7
// …
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که برای تعریف خاصیت `HTMLMediaElement.currentTime` استفاده شده است
- {{domxref("HTMLMediaElement.fastSeek()")}}: روش دیگری برای تنظیم زمان
- {{domxref("HTMLMediaElement.duration")}}: طول مدت رسانه بر حسب ثانیه