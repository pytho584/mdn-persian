---
title: "Navigator: mediaSession property"
short-title: mediaSession
slug: Web/API/Navigator/mediaSession
page-type: web-api-instance-property
browser-compat: api.Navigator.mediaSession
---

{{APIRef("Media Session API")}}

خاصیت فقط خواندنی **`mediaSession`** از رابط {{domxref("Navigator")}} یک شیء {{domxref("MediaSession")}} برمی‌گرداند که می‌توان از آن برای اشتراک‌گذاری فراداده (metadata) و سایر اطلاعات مربوط به وضعیت پخش فعلی رسانه‌ای که توسط یک سند مدیریت می‌شود، با مرورگر استفاده کرد.

این اطلاعات ممکن است به نوبه خود با دستگاه و/یا سیستم عامل به اشتراک گذاشته شود تا تجربه کاربری استاندارد کنترل رسانه دستگاه، پخش رسانه را توصیف و کنترل کند.

علاوه بر این، رابط `MediaSession` متد {{domxref("MediaSession.setActionHandler", "setActionHandler()")}} را ارائه می‌دهد که به شما امکان می‌دهد وقتی کاربر با کنترل‌های دستگاه مانند دکمه‌های پخش، توقف، جستجو و سایر کنترل‌های مشابه (چه روی صفحه و چه فیزیکی) تعامل می‌کند، رویدادهایی دریافت کنید. برای مثال، یک برنامه رادیوی اینترنتی می‌تواند از `setActionHandler()` استفاده کند تا کنترل‌های رسانه روی صفحه‌کلید یا جای دیگری از دستگاه کاربر برای کنترل پخش رسانه برنامه استفاده شود.

## مقدار

یک شیء {{domxref("MediaSession")}} که سند فعلی می‌تواند از آن برای اشتراک‌گذاری اطلاعات درباره رسانه‌ای که در حال پخش است و وضعیت پخش فعلی آن استفاده کند. این اطلاعات می‌تواند شامل فراداده‌های معمولی مانند عنوان، هنرمند و نام آلبوم آهنگ در حال پخش و همچنین احتمالاً یک یا چند تصویر حاوی مواردی مانند جلد آلبوم، عکس هنرمند و غیره باشد.

## مثال‌ها

در این مثال، فراداده به شیء `mediaSession` ارسال می‌شود. توجه داشته باشید که کد قبل از تلاش برای استفاده از `navigator.mediaSession`، ابتدا از در دسترس بودن آن اطمینان حاصل می‌کند.

```js
if ("mediaSession" in navigator) {
  navigator.mediaSession.metadata = new MediaMetadata({
    title: "Podcast Episode Title",
    artist: "Podcast Host",
    album: "Podcast Name",
    artwork: [{ src: "podcast.jpg" }],
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}