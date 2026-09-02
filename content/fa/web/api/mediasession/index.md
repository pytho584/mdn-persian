---
title: MediaSession
slug: Web/API/MediaSession
page-type: web-api-interface
browser-compat: api.MediaSession
---

{{APIRef("Media Session API")}}

رابطهٔ **`MediaSession`** از {{domxref("Media Session API", "", "", "nocode")}} به صفحه‌های وب اجازه می‌دهد رفتارهای سفارشی برای تعامل‌های استاندارد پخش رسانه فراهم کنند و فراداده‌ای را گزارش دهند که عامل کاربر می‌تواند برای نمایش در عناصر رابط کاربری استاندارد به دستگاه یا سیستم‌عامل ارسال کند.

برای مثال، یک گوشی هوشمند ممکن است پنلی استاندارد در صفحه‌قفل خود داشته باشد که کنترل‌هایی برای پخش رسانه و نمایش اطلاعات ارائه می‌دهد. مرورگر روی دستگاه می‌تواند از `MediaSession` استفاده کند تا پخش مرورگر از آن رابط کاربری استاندارد/سراسری قابل کنترل باشد.

## ویژگی‌های نمونه

- {{domxref("MediaSession.metadata", "metadata")}}
  - : یک نمونه از {{domxref("MediaMetadata")}} برمی‌گرداند که فرادادهٔ غنی رسانه را برای نمایش در رابط کاربری پلتفرم شامل می‌شود.
- {{domxref("MediaSession.playbackState", "playbackState")}}
  - : نشان می‌دهد که نشست رسانه‌ای فعلی در حال پخش است یا خیر. مقادیر معتبر عبارت‌اند از `none`، `paused` یا `playing`.

## روش‌های نمونه

- {{domxref("MediaSession.setActionHandler", "setActionHandler()")}}
  - : یک کنترل‌کنندهٔ اقدام (action handler) برای یک اقدام نشست رسانه‌ای مانند پخش یا توقف موقت (play یا pause) تنظیم می‌کند.
- {{domxref("MediaSession.setCameraActive", "setCameraActive()")}}
  - : به عامل کاربر اعلام می‌کند که آیا دوربین کاربر فعال در نظر گرفته می‌شود یا نه.
- {{domxref("MediaSession.setMicrophoneActive", "setMicrophoneActive()")}}
  - : به عامل کاربر اعلام می‌کند که آیا میکروفون کاربر در حال حاضر بی‌صدا در نظر گرفته می‌شود یا نه.
- {{domxref("MediaSession.setPositionState", "setPositionState()")}}
  - : موقعیت و سرعت پخش فعلی رسانه‌ای را که در حال ارائه است تنظیم می‌کند.
- {{domxref("MediaSession.setScreenshareActive", "setScreenshareActive()")}} {{experimental_inline}}
  - : وضعیت مورد نظر صفحه را برای اشتراک‌گذاری صفحه (screenshare) به عامل کاربر اعلام می‌کند.

## مثال‌ها

### تنظیم کنترل‌کننده‌های اقدام برای یک پخش‌کنندهٔ موسیقی

مثال زیر یک نشست رسانه‌ای جدید می‌سازد و کنترل‌کننده‌های اقدام را به آن اختصاص می‌دهد:

```js
if ("mediaSession" in navigator) {
  navigator.mediaSession.metadata = new MediaMetadata({
    title: "Unforgettable",
    artist: "Nat King Cole",
    album: "The Ultimate Collection (Remastered)",
    artwork: [
      {
        src: "https://dummyimage.com/96x96",
        sizes: "96x96",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/128x128",
        sizes: "128x128",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/192x192",
        sizes: "192x192",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/256x256",
        sizes: "256x256",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/384x384",
        sizes: "384x384",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/512x512",
        sizes: "512x512",
        type: "image/png",
      },
    ],
  });

  navigator.mediaSession.setActionHandler("play", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("pause", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("stop", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("seekbackward", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("seekforward", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("seekto", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("previoustrack", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("nexttrack", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("skipad", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("togglecamera", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("togglemicrophone", () => {
    /* کد حذف شده است. */
  });
  navigator.mediaSession.setActionHandler("hangup", () => {
    /* کد حذف شده است. */
  });
}
```

مثال زیر دو تابع برای پخش و توقف موقت تنظیم می‌کند و سپس آن‌ها را با کنترل‌کننده‌های اقدام مرتبط به‌عنوان تابع بازخواست (callback) استفاده می‌کند.

```js
const actionHandlers = [
  // play
  [
    "play",
    async () => {
      // play our audio
      await audioEl.play();
      // set playback state
      navigator.mediaSession.playbackState = "playing";
      // update our status element
      updateStatus(allMeta[index], "Action: play  |  Track is playing…");
    },
  ],
  [
    "pause",
    () => {
      // pause out audio
      audioEl.pause();
      // set playback state
      navigator.mediaSession.playbackState = "paused";
      // update our status element
      updateStatus(allMeta[index], "Action: pause  |  Track has been paused…");
    },
  ],
];

for (const [action, handler] of actionHandlers) {
  try {
    navigator.mediaSession.setActionHandler(action, handler);
  } catch (error) {
    console.log(`The media session action "${action}" is not supported yet.`);
  }
}
```

### استفاده از کنترل‌کننده‌های اقدام برای کنترل یک ارائهٔ اسلاید

کنترل‌کننده‌های اقدام «اسلاید قبلی» (`"previousslide"`) و «اسلاید بعدی» (`"nextslide"`) می‌توانند برای جابه‌جایی به جلو و عقب در یک ارائهٔ اسلاید استفاده شوند؛ مثلاً وقتی کاربر ارائهٔ خود را در یک پنجرهٔ {{domxref("Picture-in-Picture API", "Picture-in-Picture", "", "nocode")}} قرار می‌دهد و کنترل‌های مرورگر را برای مرور اسلایدها فشار می‌دهد.

```js
try {
  navigator.mediaSession.setActionHandler("previousslide", () => {
    log('> User clicked "Previous Slide" icon.');
    if (slideNumber > 1) slideNumber--;
    updateSlide();
  });
} catch (error) {
  log('Warning! The "previousslide" media session action is not supported.');
}

try {
  navigator.mediaSession.setActionHandler("nextslide", () => {
    log('> User clicked "Next Slide" icon.');
    slideNumber++;
    updateSlide();
  });
} catch (error) {
  log('Warning! The "nextslide" media session action is not supported.');
}
```

برای یک مثال عملی، به [نمونهٔ ارائهٔ اسلاید / Media Session](https://googlechrome.github.io/samples/media-session/slides.html) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}