---
title: "MediaSession: setActionHandler() method"
short-title: setActionHandler()
slug: Web/API/MediaSession/setActionHandler
page-type: web-api-instance-method
browser-compat: api.MediaSession.setActionHandler
---

{{APIRef("Media Session API")}}

متد **`setActionHandler()`** در رابط {{domxref("MediaSession")}} یک کنترل‌کننده (handler) برای یک اقدام رسانه‌ای تنظیم می‌کند. این اقدامات به برنامه‌های وب امکان می‌دهند وقتی کاربر از کنترل‌های رسانه‌ای فیزیکی یا روی‌صفحه‌ای داخلی دستگاه مانند دکمه‌های پخش، توقف یا جستجو استفاده می‌کند، اعلان دریافت کنند.

## نحو (Syntax)

```js-nolint
setActionHandler(type, callback)
```

### پارامترها

- `type`
  - : یک رشته که نوع اقدامی را که باید به آن گوش داد را نشان می‌دهد. یکی از مقادیر زیر خواهد بود:
    - `enterpictureinpicture`
      - : باز کردن رسانه در پنجره [حالت تصویر-در-تصویر](/en-US/docs/Web/API/Picture-in-Picture_API) یا [تصویر-در-تصویر سند](/en-US/docs/Web/API/Document_Picture-in-Picture_API).
    - `hangup`
      - : پایان دادن به یک تماس.
    - `nextslide`
      - : رفتن به اسلاید بعدی، هنگام ارائه یک مجموعه اسلاید.
    - `nexttrack`
      - : پیش بردن پخش به قطعه بعدی.
    - `pause`
      - : توقف موقت پخش رسانه.
    - `play`
      - : شروع (یا ادامه) پخش رسانه.
    - `previousslide`
      - : رفتن به اسلاید قبلی، هنگام ارائه یک مجموعه اسلاید.
    - `previoustrack`
      - : بازگشت به قطعه قبلی.
    - `seekbackward`
      - : جستجوی عقب در رسانه از موقعیت فعلی.
        ویژگی `seekOffset` که به تابع بازخوانی (callback) ارسال می‌شود، مقدار زمانی را که باید به عقب جستجو شود مشخص می‌کند.
    - `seekforward`
      - : جستجوی جلو از موقعیت فعلی در رسانه.
        ویژگی `seekOffset` که به تابع بازخوانی ارسال می‌شود، مقدار زمانی را که باید به جلو جستجو شود مشخص می‌کند.
    - `seekto`
      - : انتقال موقعیت پخش به زمان مشخص‌شده در رسانه.
        زمانی که باید به آن منتقل شود در ویژگی `seekTime` که به تابع بازخوانی ارسال می‌شود مشخص می‌گردد.
        اگر قصد دارید چندین عملیات `seekto` را پشت سر هم و سریع انجام دهید، می‌توانید ویژگی `fastSeek` را نیز با مقدار `true` به تابع بازخوانی ارسال کنید.
        این کار به مرورگر اجازه می‌دهد بداند که می‌تواند برای بهینه‌سازی عملیات تکراری گام بردارد و به احتمال زیاد به بهبود عملکرد منجر می‌شود.
    - `skipad`
      - : رد کردن تبلیغ یا آگهی بازرگانی که در حال پخش است.
        این اقدام ممکن است بسته به پلتفرم و {{Glossary("user agent", "عامل کاربر")}} در دسترس باشد یا نباشد، یا ممکن است به دلیل سطح اشتراک یا شرایط دیگر غیرفعال شده باشد.
    - `stop`
      - : توقف کامل پخش.
    - `togglecamera`
      - : روشن یا خاموش کردن دوربین فعال کاربر.
    - `togglemicrophone`
      - : قطع یا وصل کردن میکروفون کاربر.
    - `togglescreenshare`
      - : روشن یا خاموش کردن اشتراک‌گذاری صفحه فعال کاربر.
- `callback`
  - : تابعی که هنگام فراخوانی نوع اقدام مشخص‌شده اجرا می‌شود. تابع بازخوانی نباید مقداری برگرداند. تابع بازخوانی یک شیء شامل ویژگی‌های زیر دریافت می‌کند:
    - `action`
      - : یک رشته که نوع اقدام را نشان می‌دهد. این ویژگی به یک تابع بازخوانی واحد اجازه می‌دهد چند نوع اقدام را مدیریت کند.
    - `enterPictureInPictureReason` {{optional_inline}}
      - : این ویژگی در صورتی در دسترس خواهد بود که اقدام [`enterpictureinpicture`](#enterpictureinpicture) باشد.
        این یک مقدار شمارشی است که دلیلی را نشان می‌دهد که مرورگر این اقدام را فعال کرده است. مقادیر ممکن عبارتند از:
        - `contentoccluded`
          - : صفحه‌ای که رسانه را نمایش می‌دهد پوشیده شده است، مثلاً به دلیل تغییر برگه یا کوچک‌سازی پنجره.
        - `useraction`
          - : کاربر اقدام صریحی برای فعال کردن حالت تصویر-در-تصویر انجام داده است، مانند انتخاب گزینه «تصویر-در-تصویر» از منوی زمینه یا رابط مرورگر.
        - `other`
          - : دلیل ورود به حالت تصویر-در-تصویر چیزی است که توسط مقادیر دیگر پوشش داده نمی‌شود.
    - `fastSeek` {{optional_inline}}
      - : یک اقدام [`seekto`](#seekto) می‌تواند _به‌صورت اختیاری_ این ویژگی را شامل شود، که یک مقدار بولی است نشان می‌دهد آیا جستجوی «سریع» انجام شود یا نه.
        جستجوی «سریع» به جستجویی گفته می‌شود که در یک توالی سریع انجام می‌شود، مانند زمانی که در حال جلو یا عقب بردن سریع رسانه هستید و به سرعت از آن عبور می‌کنید.
        این ویژگی می‌تواند برای نشان دادن اینکه باید از کوتاه‌ترین روش ممکن برای جستجو در رسانه استفاده کنید به کار رود.
        در این شرایط، `fastSeek` در آخرین اقدام از توالی جستجو قرار نمی‌گیرد.
    - `seekOffset` {{optional_inline}}
      - : اگر `action` یکی از مقادیر [`seekforward`](#seekforward) یا [`seekbackward`](#seekbackward) باشد و این ویژگی موجود باشد، یک مقدار اعشاری است که تعداد ثانیه‌هایی را نشان می‌دهد که موقعیت پخش به جلو یا عقب منتقل شود.
        اگر این ویژگی موجود نباشد، آن اقدامات باید یک فاصله پیش‌فرض منطقی برای پرش به جلو یا عقب انتخاب کنند (مثلاً ۷ یا ۱۰ ثانیه).
    - `seekTime` {{optional_inline}}
      - : اگر `action` مقدار [`seekto`](#seekto) باشد، این ویژگی باید موجود باشد و باید یک مقدار اعشاری باشد که زمان مطلق در رسانه را نشان می‌دهد که موقعیت پخش باید به آن منتقل شود، که در آن ۰ نشان‌دهنده ابتدای رسانه است. این ویژگی برای سایر انواع اقدام وجود ندارد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## توضیحات

برای حذف یک کنترل‌کننده اقدام که قبلاً تنظیم شده است، دوباره `setActionHandler()` را با مقدار `null` به عنوان `callback` فراخوانی کنید.

تابع کنترل‌کننده اقدام یک پارامتر ورودی دریافت می‌کند: یک شیء که هم نوع اقدام را ارائه می‌دهد (تا تابع مشابه بتواند چند نوع اقدام را مدیریت کند) و هم داده‌های لازم برای انجام اقدام را فراهم می‌کند.

## مثال‌ها

### تنظیم کنترل‌کننده‌های اقدام برای یک پخش‌کننده موسیقی

این مثال یک نشست رسانه‌ای جدید ایجاد می‌کند و کنترل‌کننده‌های اقدام (که کار خاصی انجام نمی‌دهند) را به آن اختصاص می‌دهد.

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
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("pause", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("stop", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekbackward", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekforward", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekto", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("previoustrack", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("nexttrack", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("skipad", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("togglecamera", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("togglemicrophone", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("hangup", () => {
    /* Code excerpted. */
  });
}
```

مثال زیر دو تابع برای پخش و توقف موقت تنظیم می‌کند و سپس از آن‌ها به عنوان تابع بازخوانی با کنترل‌کننده‌های اقدام مربوطه استفاده می‌کند.

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

این مثال از کنترل‌کننده‌های اقدام مناسب برای امکان جستجو در هر دو جهت در رسانه در حال پخش استفاده می‌کند.

```js
navigator.mediaSession.setActionHandler("seekbackward", (evt) => {
  // User clicked "Seek Backward" media notification icon.
  let skipTime = evt.seekOffset || 10; // Time to skip in seconds
  audio.currentTime = Math.max(audio.currentTime - skipTime, 0);
});

navigator.mediaSession.setActionHandler("seekforward", (evt) => {
  // User clicked "Seek Forward" media notification icon.
  let skipTime = evt.seekOffset || 10; // Time to skip in seconds
  audio.currentTime = Math.min(audio.currentTime + skipTime, audio.duration);
});
```

برای حذف یک کنترل‌کننده اقدام رسانه‌ای، آن را برابر با `null` قرار دهید.

```js
navigator.mediaSession.setActionHandler("nexttrack", null);
```

### پشتیبانی از چند اقدام در یک تابع کنترل‌کننده

در صورت تمایل می‌توانید از یک تابع واحد برای مدیریت چند نوع اقدام استفاده کنید، با بررسی مقدار ویژگی `action`:

```js
let skipTime = 7;

navigator.mediaSession.setActionHandler("seekforward", handleSeek);
navigator.mediaSession.setActionHandler("seekbackward", handleSeek);

function handleSeek(details) {
  switch (details.action) {
    case "seekforward":
      audio.currentTime = Math.min(
        audio.currentTime + skipTime,
        audio.duration,
      );
      break;
    case "seekbackward":
      audio.currentTime = Math.max(audio.currentTime - skipTime, 0);
      break;
  }
}
```

در اینجا، تابع `handleSeek()` هر دو اقدام `seekbackward` و `seekforward` را مدیریت می‌کند.

### استفاده از کنترل‌کننده‌های اقدام برای کنترل ارائه اسلاید

کنترل‌کننده‌های اقدام `"previousslide"` و `"nextslide"` می‌توانند برای مدیریت حرکت به جلو و عقب در یک ارائه اسلاید استفاده شوند، مثلاً وقتی کاربر ارائه خود را در یک پنجره {{domxref("Picture-in-Picture API", "تصویر-در-تصویر", "", "nocode")}} قرار می‌دهد و کنترل‌های ارائه‌شده توسط مرورگر را برای پیمایش بین اسلایدها فشار می‌دهد.

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

برای یک مثال عملی، به [ارائه اسلاید / نمونه نشست رسانه‌ای](https://googlechrome.github.io/samples/media-session/slides.html) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}