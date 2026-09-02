---
title: "Media Session API"
---

---
title: Media Session API
slug: Web/API/Media_Session_API
page-type: web-api-overview
browser-compat: api.MediaSession
---

{{DefaultAPISidebar("Media Session API")}}

**Media Session API** راهی برای سفارشی‌سازی اعلان‌های رسانه‌ای فراهم می‌کند. این کار را با ارائهٔ فراداده (metadata) به عامل کاربر (user agent) انجام می‌دهد تا رسانه‌ای را که برنامهٔ وب شما در حال پخش آن است نمایش دهد.

همچنین هندلرهای اکشن (action handlers) را در اختیار مرورگر قرار می‌دهد تا بتواند از کلیدهای رسانه‌ای پلتفرم استفاده کند؛ کلیدهای سخت‌افزاری روی صفحه‌کلیدها، هدفون‌ها و کنترل‌های از راه دور، و کلیدهای نرم‌افزاری در ناحیهٔ اعلان‌ها و صفحهٔ قفل دستگاه‌های همراه. بنابراین حتی وقتی به صفحهٔ وب نگاه نمی‌کنید، می‌توانید رسانهٔ ارائه‌شده توسط وب را بدون وقفه و به‌طور یکپارچه از طریق دستگاه خود کنترل کنید.

هدف این است که کاربران بدون نیاز به باز کردن صفحهٔ خاصی که رسانه را اجرا کرده، بدانند چه چیزی در حال پخش است و بتوانند آن را کنترل کنند. برای پشتیبانی از Media Session API، مرورگر ابتدا به سازوکاری نیاز دارد که از طریق آن به کنترل‌های رسانه در سطح سیستم‌عامل دسترسی پیدا کند و توسط آن‌ها کنترل شود (مانند MediaControl در فایرفاکس).

## مفاهیم و کاربرد Media Session

رابط {{domxref("MediaMetadata")}} به وب‌سایت‌ها امکان می‌دهد فرادادهٔ کاملی را در اختیار رابط کاربری پلتفرم قرار دهند تا برای رسانه‌ای که در حال پخش است نمایش داده شود. این فراداده شامل عنوان، نام هنرمند (پدیدآور)، نام آلبوم (مجموعه)، آثار هنری (جلد) و اطلاعات فصل‌ها است. پلتفرم‌ها می‌توانند این فراداده را در مراکز رسانه، اعلان‌ها، صفحه‌های قفل دستگاه و موارد مشابه نمایش دهند. برای مثال، دستگاه‌های مختلف ممکن است داده‌های Media Session API را به این شکل نمایش دهند:

![تصویری که داده‌های Media Session را برای عنوان و آثار هنری تریلر Sintel در یک مرورگر رومیزی، گوشی موبایل و ساعت هوشمند نشان می‌دهد](media-session-ui.jpg)

> [!CALLOUT]
> منبع اصلی تصویر: [Customize media notifications and playback controls with the Media Session API](https://web.dev/articles/media-session) در web.dev (۲۰۲۴)

رابط {{domxref("MediaSession")}} به کاربران امکان می‌دهد پخش رسانه را از طریق عناصر رابط کاربری تعریف‌شده توسط عامل کاربر کنترل کنند. تعامل با این عناصر، هندلرهای اکشن را در صفحه‌ای که رسانه را پخش می‌کند فعال می‌کند. از آنجا که چندین صفحه ممکن است به‌طور هم‌زمان از این API استفاده کنند، عامل کاربر مسئول فراخوانی هندلرهای اکشن صفحهٔ درست است. اگر رفتاری از سوی صفحه تعریف نشده باشد، عامل کاربر رفتارهای پیش‌فرض را ارائه می‌کند.

## دسترسی به Media Session API

رابط اصلی Media Session API، رابط {{domxref("MediaSession")}} است. به‌جای ساخت نمونهٔ `MediaSession` اختصاصی خودتان، از طریق ویژگی {{domxref("navigator.mediaSession")}} به API دسترسی پیدا می‌کنید. برای مثال، برای تنظیم وضعیت کنونی جلسهٔ رسانه روی حالت `playing`:

```js
navigator.mediaSession.playbackState = "playing";
```

## رابط‌ها

- {{domxref("ChapterInformation")}}
  - : فرادادهٔ مربوط به یک فصل جداگانه از یک منبع رسانه‌ای (یعنی یک فایل ویدیویی یا صوتی) را نشان می‌دهد.
- {{domxref("MediaMetadata")}}
  - : به صفحهٔ وب اجازه می‌دهد فرادادهٔ رسانه‌ای کاملی را برای نمایش در رابط کاربری پلتفرم فراهم کند.
- {{domxref("MediaSession")}}
  - : به صفحهٔ وب اجازه می‌دهد رفتارهای سفارشی برای تعاملات استاندارد پخش رسانه ارائه کند.

## مثال‌ها

### راه‌اندازی هندلرهای اکشن برای یک پخش‌کنندهٔ موسیقی

مثال زیر تشخیص قابلیت (feature detection) را برای Media Session API نشان می‌دهد. سپس یک شیء فراداده برای جلسه می‌سازد و هندلرهای اکشن را برای کنش‌های کنترلی کاربر اضافه می‌کند:

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

برخی عامل‌های کاربر در دستگاه‌های همراه، پخش خودکار عناصر رسانه‌ای را غیرفعال می‌کنند و برای شروع پخش به یک ژست کاربر نیاز دارند. مثال زیر یک رویداد `pointerup` را به دکمهٔ پخش داخل صفحه اضافه می‌کند که سپس برای شروع کد مربوط به جلسهٔ رسانه استفاده می‌شود:

```js
playButton.addEventListener("pointerup", (event) => {
  const audio = document.querySelector("audio");

  // User interacted with the page. Let's play audio!
  audio
    .play()
    .then(() => {
      /* Set up media session controls, as shown above. */
    })
    .catch((error) => {
      console.error(error);
    });
});
```

### استفاده از هندلرهای اکشن برای کنترل یک ارائهٔ اسلایدی

از هندلرهای اکشن `"previousslide"` و `"nextslide"` می‌توان برای حرکت به جلو و عقب در یک ارائهٔ اسلایدی استفاده کرد؛ برای مثال، وقتی کاربر ارائه‌اش را در پنجرهٔ {{domxref("Picture-in-Picture API", "Picture-in-Picture", "", "nocode")}} قرار می‌دهد و کنترل‌های مربوط به پیمایش بین اسلایدها را که مرورگر ارائه کرده است فشار می‌دهد.

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

برای مشاهدهٔ یک مثال عملی، نمونهٔ [Presenting Slides / Media Session Sample](https://googlechrome.github.io/samples/media-session/slides.html) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Customize media notifications and playback controls with the Media Session API](https://web.dev/articles/media-session) در web.dev (۲۰۲۴)